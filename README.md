# Java Interview Questions & Answers

### Table of contents

| No | Questions|
| -- | -------- |
| 1 |[How to Manage exceptions with Completable Futures?](#How-to-Manage-exception-with-completable-futures?)|
| 2 |[Explain the difference between findAny and findFirst, and when would you prefer one over the other?](#explain-the-difference-between-findany-and-findfirst-and-when-would-you-prefer-one-over-the-other)|
| 3 | [When would you use Parallel Streams and why?](#when-would-you-use-parallel-streams-and-why)|
| 4 | [What if you have a list of Orders and each Order contains Edibles Fruits with quantities and prices. You want to find the total amount spent on each Fruit across all orders](#what-if-you-have-a-list-of-orders-and-each-order-contains-edibles-fruits-with-quantities-and-prices-you-want-to-find-the-total-amount-spent-on-each-fruit-across-all-orders)|
| 5 | [How do you stream a file?](#how-do-you-stream-a-file)|
| 6 | [What is the purpose of the peek method in a Stream?](#what-is-the-purpose-of-the-peek-method-in-a-stream)|
| 7 | [How do you convert a Stream to an array?](#how-do-you-convert-a-stream-to-an-array)|
| 8 | [How can you find the average salary for all the employees who have salary greater than 50000 in each department](#how-can-you-find-the-average-salary-for-all-the-employees-who-have-salary-greater-than-50000-in-each-department)|


1. ### How to Manage exceptions with Completable Futures?
   ![Screenshot] (images/completable-feature.png)

   There are several methods to handle exceptions with completable future.
   We can use methods like

   <em>exceptionally(Function<Throwable, T> fn)</em>

   <em>handle(BiFunction <? super T, Throwable, ? extends U>fn)</em>

   <em>whenCompelte</em>

   <em>whenCompleteAsync</em>
   
   These methods help in creating robust asynchronous systems by allowing you to specify error-handling behavior explicitly.
   
   **Below is an example of using exceptionally**

   ```java
      CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
         if (Math.random() < 0.5) {
         throw new RuntimeException("Run Time Exception!");
         }
         return "Success";
      }).exceptionally(ex -> "Error: " + ex.getMessage());

      future.thenAccept(System.out::println);
   ```
   **Below is an example of using handle**

   ```java
      CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
         if (Math.random() > 0.5) throw new RuntimeException("Error!");
            return "Hello";
         }).handle((result, ex) -> {
         if (ex != null) {
         return "Failed due to: " + ex.getMessage();
         }
         return result;
      });

      future.thenAccept(System.out::println);
   ```

   **Exception Handling using whenCompelte and whenCompleteAsync:**
   whenCompelte is executed in the same thread that completes the CompletableFuture or the caller thread if the future is already complete.

   whenCompelteAsync allows the completion handler to run in a different thread provided by the Executor or the default asynchronous execution facility.

   The choice between them depends on whether you need the non-blocking behavior and are willing to handle tasks in a separate thread

   **Below are the example of using whenCompelte and whenCompleteAsync**

   ```java
      CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> {
         if (Math.random() > 0.5) throw new RuntimeException("Operation failed");
         return "Operation succeeded";
      }).whenComplete((result, ex) -> {
         if (ex != null) {
         System.out.println("Error: " + ex.getMessage());
         } else {
         System.out.println(result);
         }
      });
   ```

   ```java
      // Example of whenCompleteAsync
      CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
         if (Math.random() > 0.5) throw new RuntimeException("Operation failed");
         return "Operation succeeded";
      }).whenCompleteAsync((result, ex) -> {
         if (ex != null) {
            System.out.println("Error: " + ex.getMessage());
         } else {
            System.out.println(result);
         }
      });
   ```

   **[⬆ Back to Top](#table-of-contents)**
   
2. ### Explain the difference between findAny and findFirst, and when would you prefer one over the other?
   
   **findFirst** returns the first element of the stream, respecting the encounter order if one exists.

   **findAny** can return any element from the stream, and it's more performance-friendly in parallel streams because it doesn't enforce processing order.

   **[⬆ Back to Top](#table-of-contents)**

3. ### When would you use Parallel Streams and why?

   We would use Parallel stream if
   - We have a lot of data to process in the same (or a very similar) way.
   - Ordering doesn’t matter.
   - Items are independent of each other.
   - if particular processing step is the bottleneck.
   
   Lets find the Sum of large list of integers.
   ```java
      package collectors;

      import java.util.ArrayList;
      import java.util.List;
      import java.util.Random;

      public class ParallelStreamsDemo {

        public static void main(String[] args) {
            // Create a large list of random integers
            List<Integer> numbers = new ArrayList<>();
            Random random = new Random();
            for (int i = 0; i < 1_000_000; i++) {
                numbers.add(random.nextInt(100));
            }

            // Calculate the sum using parallel stream
            long startTime = System.currentTimeMillis();
            int sum = numbers.parallelStream().reduce(0, Integer::sum);
            long endTime = System.currentTimeMillis();

            System.out.println("Sum: " + sum);
            System.out.println("Time taken with parallel stream: " + (endTime - startTime) + " ms");
        }
      }
   ```
   **[⬆ Back to Top](#table-of-contents)**

4. ### What if you have a list of Orders and each Order contains Edibles Fruits with quantities and prices. You want to find the total amount spent on each Fruit across all orders
   This requires some skills of grouping and summarizing.

   **Orders Model**
   ```java
      package collectors.model;

      import java.util.List;

      class Orders {
         List<Item> items;
         
      }
   ```
   **Item Model**
   ```java
      package collectors.model;

      public class Item {
         String name;
         double price;
      }
   ```
   **Results:**Below is the total price for each Fruit for all the orders.

   ```java
      package collectors;

      import collectors.model.Item;
      import collectors.model.Orders;

      import java.util.Arrays;
      import java.util.List;
      import java.util.Map;
      import java.util.stream.Collectors;

      public class ItemPriceAggregator {

         public static void main(String[] args) {

            List<Orders> orders = Arrays.asList(new Orders(Arrays.asList(new Item("Pears",200.45, 22),new Item("Mangoes",120.45, 45),new Item("Oranges",145.67, 22),new Item("Mandarins",207.45, 89))),
                     new Orders(Arrays.asList(new Item("Pears",200.45, 21),new Item("Mangoes",120.45, 459),new Item("Oranges",345.67, 22),new Item("Mandarins",207.45, 89))));

            Map<String, Double> totalAmountPerItem = orders.stream()
                     .flatMap(order -> order.items.stream())
                     .collect(Collectors.groupingBy(Item::getName,
                              Collectors.summingDouble(item -> item.price * item.quantity)));
            totalAmountPerItem.entrySet().stream()
                     .forEach(entry -> System.out.println(entry.getKey() + " = " + entry.getValue()));

         }
      }
   ```
   **[⬆ Back to Top](#table-of-contents)**
5. ### How do you stream a file?
   ```java
      Stream<String> lines = Files.lines(Paths.get("file.txt"));
   ```
   **[⬆ Back to Top](#table-of-contents)**

6. ### What is the purpose of the peek method in a Stream?
   peek is an intermediate operation used mainly for debugging purposes, as it allows you to perform an operation on each element of the stream as it's consumed.

   peek is used to

   >Observing Elements: is often used to observe the elements of the stream at a certain point in the pipeline.</m>

   This is particularly useful for debugging complex stream operations to understand how elements are transformed as they pass through various stages of the stream.

   >Logging: peek can be used to log information about the elements for debugging purposes without altering the stream's processing.
   Let’s say we have a list of integers, and we want to filter out numbers less than 10, map them to their squares, and then collect them into a list.

   While we are doing this we want to see the element after filtering and also after mapping. Lets look at the below example.
   ```java
      import java.util.Arrays;
      import java.util.List;
      import java.util.stream.Collectors;

      public class PeekExample {
         public static void main(String[] args) {
            List<Integer> numbers = Arrays.asList(1, 5, 10, 15, 20);

            List<Integer> squaredNumbers = numbers.stream()
                  .filter(n -> n >= 10)
                  .peek(n -> System.out.println("After filter: " + n))
                  .map(n -> n * n)
                  .peek(n -> System.out.println("After map: " + n))
                  .collect(Collectors.toList());
         }
      }
   ```
   In the above example we are peeking the elements to log them at each stage that could also be used for debugging purpose.

   **[⬆ Back to Top](#table-of-contents)**

7. ### How do you convert a Stream to an array?
   ```java
      String[] array = stream.toArray(String[]::new);
   ```

8. ### How can you find the average salary for all the employees who have salary greater than 50000 in each department

   **Employee Model**
   ```java
      package collectors.model;

      import lombok.AllArgsConstructor;
      import lombok.Getter;
      import lombok.NoArgsConstructor;
      import lombok.Setter;

      import java.math.BigDecimal;
      @Getter
      @Setter
      @AllArgsConstructor
      @NoArgsConstructor
      public class Employee {
         private String name;
         private Department department;
         private BigDecimal salary;

      }
   ```

   **Department Model**
   ```java
      import lombok.AllArgsConstructor;
      import lombok.Getter;
      import lombok.NoArgsConstructor;
      import lombok.Setter;

      @Getter
      @Setter
      @AllArgsConstructor
      @NoArgsConstructor
      public class Department {
         private String name;

      }
   ```
   **Finding average salary in each department greater than 50000.**

   ```java
      package collectors.model;

      import java.math.BigDecimal;
      import java.util.Arrays;
      import java.util.List;
      import java.util.Map;
      import java.util.stream.Collectors;

      public class AverageSalaryByDept {
         public static void main(String[] args) {
            List<Employee> employees = Arrays.asList(new Employee("Vikas",new Department("IT"),new BigDecimal(212345.67)),
                     new Employee("Ravi",new Department("Commercial"),new BigDecimal(12345.67)),
                     new Employee("Rajni",new Department("Procurment"),new BigDecimal(322345.67)),
                     new Employee("Sinha",new Department("Commercial"),new BigDecimal(42345.67)));

            Map<Department, Double> averageSalaryByDepartment = employees.stream()
                     .filter(e -> e.getSalary().compareTo(new BigDecimal("50000")) > 0)
                     .collect(Collectors.groupingBy(Employee::getDepartment,
                              Collectors.mapping(Employee::getSalary,
                                    Collectors.averagingDouble(BigDecimal::doubleValue))));

            averageSalaryByDepartment.entrySet().stream()
                     .forEach(entry -> System.out.println(entry.getKey().getName() + " = " + entry.getValue()));
         }
      }
   ```
