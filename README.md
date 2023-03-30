# Hello-World
Say Hello to the world of everything

# Getting Started
* **THE C PROGRAMMING LANGUAGE** by Brian W. Kernighan and Dennis M. Ritchie.
  > The only way to learn a new programming language is by writing programs in it.

* The first program to say "Hello, World!"
    ```C
      #include <stdio.h>

      int main(void) {
          printf("Hello, World!");

          return 0;
      }
    ```

# Markdown
```
Heading                   # H1
                          ## H2
                          ### H3

Bold                      **bold text**
Italic                    *italiciez text*
Blockquote                > blockquote

Ordered List              1. First item
                          2. Second item
                          3. Third item

Unordered List            - First item
                          - Second item
                          - Third item

Code                      `code`
Horizontal Rule           ---
Link                      [title](https://www.example.com)
Image                     ![alt text](image.jpg)

Table                     | Syntax | Description |
                          | ------ | ----------- |
                          | Header | Title       |
                          | Paragrah | Text      |

Fenced Code Block         ```
                          {
                            "firstName": "John",
                            "lastName": "Smith",
                            "age": 25
                          }
                          ```
```

# GitHub
- a code hosting platform for version control and collaboration
  + repository
  + branch
  + commit
  + pull request

- workflow
  * fork/**New Repository**/**Import Repository**
  ![Init Repo](https://learn.microsoft.com/en-us/contribute/media/git-and-github-initial-setup.png)

  * Work on GitHub Repo or local repo - `git clone <repo-url>` or `git init <repo>`
      ```
      1. Create a branch
      2. Make changes
      3. Create a pull request
      4. Address review comments
      5. Merge your pull request
      6. Delete your branch
      ```
    ![main && feature](https://docs.github.com/assets/cb-23923/mw-1000/images/help/repository/branching.webp)
