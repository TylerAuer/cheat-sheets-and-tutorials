# JavaScript Notes

## Things to Learn More About

- Spread operators
- Generators
- Promises

## Iterators and Generators


- Generators run until they reach a `yield` statement, then they return what is paired with the `yield`, when called again (often with `generator.next()`) they continue until they reach another `yield` statement
- Generators have a `*` at the start of their name. Ex: 
  ```javascript
  function *generator() {
    let x = 1
    while (x < 100) {
      yield x
      x++
    }
  }
  ```
- `[Symbol.iterator]` sets the default iterator for an object. I used it when building a linked list `class` for the Algorithms Class:

  ```javascript
  *[Symbol.iterator]() {
      // this.head is the first node in the list
      let node = this.head;
      // null is the value for a missing node
      while (node) {
        // return the node
        // yield pauses the generator until called again
        yield node;

        // node.next returns the next node in the linked list
        node = node.next;
      }
    }
  ```