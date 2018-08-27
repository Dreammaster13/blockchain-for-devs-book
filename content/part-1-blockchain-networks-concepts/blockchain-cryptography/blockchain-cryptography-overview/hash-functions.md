# Hashing and Hash Functions

In computer programming **hash functions **map text \(or other data\) to integer numbers. Usually different inputs maps to different outputs, but sometimes a **collision** may happen \(different input with the same output\).

<div class="video-player">
  Watch the video: <a target="_blank" href="https://www.youtube.com/watch?v=FIJVl16e2tI">https://www.youtube.com/watch?v=FIJVl16e2tI</a>.
</div>
<script src="/assets/js/video.js"></script>

The process of calculating the value of certain hash function is called "**hashing**".

![](/assets/hash-function.jpg)

In the above example the text `John Smith` is hashed to the hash value `02` and `Lisa Smith` is hashed to `01`. The input texts `John Smith` and `Sandra Dee` both are hashed to `02` and this is called "**collision**".

Hash functions are **irreversible by design**, which means that there is no fast algorithm to restore the input message from its hash value.

In programming **hash functions** are used in the implementation of the data structure "**hash-table**" \(associative array\) which maps values of certain input type to values of another type, e.g. map product name \(text\) to product price \(decimal number\).

A **naive hash function **is just to sum the bytes of the input data / text. It causes a lot of collisions, e.g. `hello` and `ehllo` will have the same hash code. **Better hash functions** use the [Merkle–Damgård construction](https://en.wikipedia.org/wiki/Merkle%E2%80%93Damg%C3%A5rd_construction) scheme, which takes the first byte as **state**, then **transforms the state** \(e.g. multiplies it by a prime number like 31\), then **adds the next byte** to the state, then again transforms the state and adds the next byte, etc. This significantly reduces the rate of collisions and produces better distribution.

