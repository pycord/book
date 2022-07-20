# What is a model?
Pycords' Model's are simply classes which represent Discord Objects, such as `User`, `Guild`, `Channel`, `Message`, etc.

## General Model Design
Every model subclasses the `Hashable` class which allows for their ids to be hashed.

Model's are also designed to be replacable, meaning you can subclass and replace any model class you want.
Some model internals may also be written in Rust to greatly improve their speed and scalability.

## Help Us!
Our model design is still a big WIP, if you wanna help design it with us, [make a PR](https://github.com/pycord/book/compare)!
