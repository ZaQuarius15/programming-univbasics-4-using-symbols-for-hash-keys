# Using Symbols For Hash Keys

## Learning Goals

- Review the `Symbol` data type
- Recognize the immutability of `Symbol`s
- Compare the use of `Symbol`s and `String`s as `Hash` keys
- Recognize Ruby's alternate syntax for `Hash`es with `Symbol`s for keys

## Introduction

We know that `Hash`es are data structures comprised of key/value pairs. We also
know we can create `Hash`es simply by writing out key/value pairs wrapped in curly
braces:

```ruby
dog_one = {
  :name => "Luca",
  :breed => "German Shepherd"
}
#=> {:name=>"Luca", :breed=>"German Shepherd"}

dog_two = {
  :name => "Lola",
  :breed => "Giant Schnauzer"
}
#=> {:name=>"Lola", :breed=>"Giant Schnauzer"}
```

In the previous lessons, we mentioned that `Hash` keys can be any data type. You
also may have noticed, though, that we quickly switched to using
[`Symbols`][symbols] for our keys in most of the examples. 

In this lesson, we're going to discuss `Symbol`s and why they are ideal to use
as keys in our `Hash`es. They are so frequently preferred, in fact, that Ruby
has an alternative syntax for writing `Hash`es with `Symbol`s for keys that you
need to recognize.

## Using Symbols for Hash Keys

Just to quickly review, [`Symbols`][symbols] are a scalar data type. They share
some similarities with `String`s, but instead of being wrapped in quotations,
`Symbol`s always start with a colon (`:`):

```ruby
:i_am_a_symbol
#=> :i_am_a_symbol
```

Every piece of data, including the `Symbol` above, takes up a small amount of
memory on the computer. When we write out a `Symbol` like `:i_am_a_symbol`,
Ruby allocates some memory to that piece of data. The same is true of a
`String`. Here's the difference, for every `String` a new bit of memory is used
up for every use of a `Symbol`, we only use _the first Symbol ever created_.

So:

```ruby
x = "pizza"
y = "pizza"
z = "pizza"
```

Uses up 3 * the size of a `String`.

```ruby
x = :pizza
y = :pizza
z = :pizza
```

This only uses 1 * the size of a `Symbol` of memory. Much more efficient.

There's a lot of detail here, but but the key things to take away is that
`Symbol`s-as-keys helps keep memory footprint down.  For most programs you'll
write at Flatiron School the difference won't hurt. But in the professional
world, Rubyists prefer `Symbol`s as keys.

## Using the Alternate Hash Syntax

When using symbols for keys, we have the option of using an alternative syntax
when defining a `Hash`:

```ruby
dog_one = {
  name: "Luca",
  breed: "German Shepherd"
}
#=> {:name=>"Luca", :breed=>"German Shepherd"}

dog_two = {
  name: "Lola",
  breed: "Giant Schnauzer"
}
#=> {:name=>"Lola", :breed=>"Giant Schnauzer"}
```

A few things have changed. For starters, the symbols `:name` and `:breed` no
longer have a colon before them. Instead, they have a colon immediately
_after_, in place of the hash-rocket.

This syntax only works for keys that are symbols, but is similar in syntax to
how other languages like JavaScript write their key/value pairs.  Since Ruby
drives one of the most popular web frameworks in existence, Rails, this second
way of creating `Symbol`-keyed `Hash`es was added in order to make
interoperability easy.

Regardless of how you create the `Hash`, Ruby will still display the old
hash-rocket format.

## Conclusion

Symbols are a great choice to use for keys when constructing `Hash`es. Although
keys can be made from whatever data type we feel is best, symbols come with
some advantages. No matter how many times a symbol is written in your code, Ruby
will consider it to be the same thing, allocating just one location in memory
for the symbol.

## Resources

[immutable]: https://en.wikipedia.org/wiki/Immutable_object
