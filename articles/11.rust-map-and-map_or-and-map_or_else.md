# 11.Rust map & map\_or & map\_or\_else

在 Rust 中，`map`、`map_or` 和 `map_or_else` 是迭代器（Iterator）trait 上的方法，它们用于转换迭代器中的每个元素。这些方法在处理 `Option` 类型时特别有用，因为它们允许你定义一个转换逻辑，将 `Option<T>` 映射到 `Option<U>`。

#### map

`map` 方法接收一个闭包，该闭包接受当前迭代器中的一个元素，并返回一个新类型的元素。如果迭代器中的元素是 `Some(value)`，闭包将被调用，并且 `Some` 包装器将保持不变。如果元素是 `None`，则迭代器将返回 `None`。

```rust
let optional_number: Option<i32> = Some(10);

let mapped_optional_string = optional_number.map(|n| n.to_string());

// mapped_optional_string 的类型是 Option<String>
```

#### map\_or

`map_or` 方法也接收一个闭包，但它需要一个额外的参数，这个参数是当迭代器中的元素是 `None` 时返回的默认值。闭包返回的类型是这个默认值的类型。

```rust
let optional_number: Option<i32> = None;

let default_value = 42;

let mapped_optional_string = optional_number.map_or(default_value, |n| n * 2);

// mapped_optional_string 的值将是 42，因为 optional_number 是 None
```

#### map\_or\_else

`map_or_else` 方法与 `map_or` 类似，但它接收的闭包返回的是一个计算默认值的闭包。这在你需要根据某些条件或上下文计算默认值时非常有用。

```rust
let optional_number: Option<i32> = None;

let mapped_optional_string = optional_number.map_or_else(|| "default value", |n| n.to_string());

// mapped_optional_string 的值将是 "default value" 字符串，因为 optional_number 是 None
```

#### 比较 map\_or 和 map\_or\_else

* `map_or` 接受一个默认值和一个闭包。
* `map_or_else` 接受一个返回默认值的闭包和一个转换闭包。

当你需要一个简单的默认值时，使用 `map_or` 是方便的。但如果你需要基于某种条件或状态计算一个更复杂的默认值，`map_or_else` 会是更好的选择。

#### 示例

以下是 `map`、`map_or` 和 `map_or_else` 的一个对比示例：

```rust
let numbers: Option<Vec<i32>> = Some(vec![1, 2, 3]);

// 使用 map 将 Vec<i32> 中的每个数字乘以 2
let doubled_numbers = numbers.map(|nums| nums.iter().map(|&x| x * 2).collect::<Vec<_>>());
// doubled_numbers 的类型是 Option<Vec<i32>>

// 使用 map_or 为 None 的情况提供一个空的 Vec
let default_empty_vec = Vec::new();
let doubled_or_default_numbers = numbers.map_or(default_empty_vec, |nums| nums.iter().map(|&x| x * 2).collect::<Vec<_>>());
// doubled_or_default_numbers 的类型是 Vec<i32>

// 使用 map_or_else 为 None 的情况提供一个通过闭包计算的 Vec
let calculated_default = vec![10, 20, 30];
let doubled_or_calculated_default_numbers = numbers.map_or_else(|| calculated_default, |nums| nums.iter().map(|&x| x * 2).collect::<Vec<_>>());
// doubled_or_calculated_default_numbers 的类型是 Vec<i32>
```

在这个例子中，我们展示了如何对 `Option<Vec<i32>>` 中的数字进行操作，以及如何为 `None` 情况提供不同的默认值。
