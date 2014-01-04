---
layout: post
title: "Booby 0.5: Introducing the inspection api"
author: jaimegil
tags: [development, python, model, booby, inspect]
---

Exactly a year ago the first Booby release [was announced][booby_announce]. Today with the release of the *0.5.0* version I'm very happy to say that Booby has continued to be developed keeping its *simplicity* and *isolation* from other libraries and providing a thin and robust *abstraction layer* for data modeling and usage.

## The path taken

During the [past two versions][changes] I focused on fixing bugs and taking into account some use cases without adding so much features, and provide a *pythonic api* that would not interfere nor create undesirable side effects in the end-user application code.

The idea is to be as non-intrusive as possible and provide a *toolkit* to build your own data models, validators, serializators or wathever you need to work with your data.

And the first step to achieve this comes with the most important feature of this version and that names this post: the **Inspection api**.

## Implementing the Inspection api

With the desire of turning Booby into a toolkit for building [data-driven][data_driven_wikipedia] applications and libraries arises the need for access some internal data of Booby objects and classes, such as [model fields][models_docs].

A first approach could have been to add a public attribute (let's name it `fields`) to the `Model` class containing the model fields. Several things made me get away from this idea quickly. Some examples are:

* What happens if my data *model* should have a *fields* field?
* What happens if I want to add more public attributes accessing internal Booby data? I will finish with a base *Model* class filled with lots of attributes, so the first problem would become bigger.

That would taken me away from my goal of a *thin* and *non-intrusive* api, so I decided to look for other people's approaches for this kind of functionalities. I didn't need to look far to find two good examples: the [Python inspect][python_inspect_docs] and the [SQLAlchemy inspection][sqlalchemy_inspection_docs] modules.

I took some ideas from both modules to build the Booby one. From the SQLAlchemy module I took *its name* because I thought it would be less likely to collision with the Python module. From the Python module I took *its functional api* (although with some changes in the way functions are named) because it seems more explicit than the SQLAlchemy common `inspect` function.

All this has resulted in the `booby.inspection` module, that for now defines the `get_fields(model)` and `is_model(obj)` functions.

Take a look to the [inspection module documentation][inspection_api_docs] for more information about how these functions work.

## Future

The future of [Booby][booby_at_github] is linked with the goals exposed above: build a toolkit to model, validate, serialize and whatever you need to work with your application data, always trying to be the more pythonic and least intrusive as possible.

Some of the changes I have in mind for the next releases are:

* Decouple *validations* and *fields*. As Booby fields are not intented only to validate data I want to extract validations from fields. Of course it will be possible to validate fields, but I want to make it more decoupled.
* Extract more generic base classes (`Object` <- `Validator` <- `Model`) giving support for a more wide range of use cases.
* Take into account *data serialization/deserialization*.
* Extend the `inspection` api with more functionality.

And finally don't doubt to share your ideas here or [opening issues][booby_issues] at Github. And of course [download][booby_at_pypi] and [try Booby][booby_docs].


[booby_announce]: /2013/01/04/booby-data-modeling-and-validation.html
[changes]: https://booby.readthedocs.org/en/0.5.0/changes.html
[inspection_api_docs]: https://booby.readthedocs.org/en/0.5.0/inspection.html
[data_driven_wikipedia]: https://en.wikipedia.org/wiki/Data-driven_programming
[models_docs]: https://booby.readthedocs.org/en/0.5.0/models.html
[python_inspect_docs]: http://docs.python.org/3.3/library/inspect.html
[sqlalchemy_inspection_docs]: http://docs.sqlalchemy.org/en/rel_0_9/core/inspection.html
[booby_at_github]: https://github.com/jaimegildesagredo/booby
[booby_issues]: https://github.com/jaimegildesagredo/booby/issues
[booby_at_pypi]: https://pypi.python.org/pypi/booby
[booby_docs]: https://booby.readthedocs.org/en/0.5.0
