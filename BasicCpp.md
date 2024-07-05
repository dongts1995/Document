## C++ Basic

### Pointer and Reference:

**❓ Explain the difference between pointers and references in C++. When should you use each one?**

| Pointer   | Reference |
| --------- | ------- |
|   A pointer is a variable that holds the memory address of another variable. It can be reassigned to point to different variables and can be null (i.e., it can hold a value of `nullptr`).     |       A reference is an alias for another variable. Once a reference is initialized to a variable, it cannot be changed to refer to another variable and cannot be null.                     |
| Use pointers when you need to: <br> * Allocate memory dynamically. <br> * Change what pointer points to. <br> * Implement data structures like liked lists, trees, etc.. <br> * Pass large objects to functions whithout copying. | Use references when you: <br> * Want to avoid copying but you don't need to reassign. <br> * Are passing objects to function <br> * Need to simpler syntax and easier usage compared to poiters. |
| Impact to performance: <br> * Dereferencing a pointer can be slightly slower than accessing a variable directly due to the additional level of indirection. | Impact to performance: <br> * Accessing a reference is typically as fast as accessing the dereferencing pointer since there is no additional level of indirection |
| Impact to Memory Management: <br> * Poiters require explicit memory management. You need to manually allcate (`new`) and deallocate (`delete`) memory. Improper handling can lead to memory leaks and fragmentation. | Impact to Memory Management: <br> * References do not require explicit memory management. They do not introduce the risk of memory leaks but cannot be reseated to another variable. |

Examples:
```cpp
// Using pointer
int* p = new int(10);
delete p; // Must delete to free memory

// Using reference
int a = 10;
int& ref = a;
// No need to manage memory explicitly
```


**❓ What happens if you use an uninitialized pointer? How can you avoid this error**

If you use an uninitialized poiter, it may point to random memory location, leading to undefined behavior, crashes, or data corruption

To avoid the error:
* Alway initialize pointer befor use, either by assigning them a valid memory adress or `nullptr`
* Use smart pointers ('std::unique_ptr`, `shared_ptr`) from the C++ Standard Library which handle initialization and memory management automatically.

Example
```cpp
int* uninitializedPtr; // Uninitialized pointer

// Safe initialization
int a = 10;
int* ptr = &a; // Points to a valid memory address

// Using smart pointer
std::unique_ptr<int> smartPtr = std::make_unique<int>(10);
```

### RAII (SBRM)
Resource Acquisition Is Initialization or RAII is a C++ programming technique which binds the life cycle of a resource to the lifetime of an ofject.

Resource examples: allocated heap memory, thread of excution, open file, locked mutex, ...

RAII guarantees that:
* the resource is availabe to any function that may access the object
* All resources are released.

Self implement RAII: Encapsulate each resource into a class
* The constructor acquires the resource and estalished all class invariants oe throws an expection if that cannot be done
* The destructor releases the resource and never throws exceptions

Using RAII-classes:

`std::string`

`std::vector`

`std::jthread (C++20)`

`std::unique_ptr` `shared_ptr` through   `std::mak_unique` `std::make_shared`

`std::lock_guard` `std::unique_lock` `std::shared_lock`

❓ Can I throw an exception from a constructor? From a destructor? -> Yes


### std::optional

`std::optional` is a feature that provide a way to represent a null value.

Examples:
```cpp
std::optional<int> charToInt(char c) {
    if (c >= '0' && c <= '9') {
        return static_cast<int>(c - '0');
    } else {
        return std::nullopt;
    }
}

int main() {
    char inputChar;
    std::cin >> inputChar;

    auto result = charToInt(inputChar);
    if (result.has_value()) {
        std::cout << result.value() << std::endl;
    } else {
        std::cout << "null" << std::endl;
    }

    return 0;
}

```
or:
```cpp
std::optional<int> optValue = /* some optional value */;

// Sử dụng value_or() để tránh ngoại lệ khi không có giá trị
int result = optValue.value_or(0); // Nếu optValue rỗng, result sẽ là 0

std::optional<int> charToInt(char c) {
    if (c >= '0' && c <= '9') {
        return static_cast<int>(c - '0');
    } else {
        return std::nullopt;
    }
}

int main() {
    char inputChar;
    std::cin >> inputChar;

    auto result = charToInt(inputChar);
    std::cout << result.value(-1) << std::endl;

    return 0;
}

```



















# A first-level heading   -> `#`
## A second-level heading  -> `##`
### A third-level heading  -> `###`

**This is bold text**  -> `Ctrl+B`

_This text is italicized_ -> `Ctrl+I`

~~This was mistaken text~~ -> `~~ ~~`

This is a <sub>subscript</sub> text -> `<sub> </sub>`

This is a <sup>superscript</sup> text -> `<sup> </sup>`

Text that is not a quote

> Text that is a quote

Use `git status` to list all new or modified files that haven't yet been committed.

Some basic Git commands are:
```
git status
git add
git commit
```

The background color is `#ffffff` for light mode and `#000000` for dark mode.

This site was built using [GitHub Pages](https://pages.github.com/).

- George Washington
* John Adams
+ Thomas Jefferson


1. James Madison
2. James Monroe
3. John Quincy Adams

1. First list item
   - First nested list item
     - Second nested list item
    
- [x] #739
- [ ] https://github.com/octo-org/octo-repo/issues/740
- [ ] Add delight to the experience when all tasks are complete :tada:

@github/support What do you think about these updates?

@octocat :+1: This PR looks great - it's ready to merge! :shipit:

Here is a simple footnote[^1].

A footnote can also have multiple lines[^2].

[^1]: My reference.
[^2]: To add line breaks within a footnote, prefix new lines with 2 spaces.
  This is a second line.

> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.

<!-- This content will not appear in the rendered Markdown -->

Let's rename \*our-new-project\* to \*our-old-project\*.


```cpp
#include <iostream>

int main()
{
    std::cout<<"Hello World";

    return 0;
}
```
