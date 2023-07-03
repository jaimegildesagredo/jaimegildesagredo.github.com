---
layout: post
title: "Booby: data modeling and validation"
author: jaimegil
tags: [development, finch, python, ddd, model, data]
---

Today I'm glad to announce the first public release of [Booby][booby_02], a standalone data *modeling* and *validation* library written in Python and licensed under the [Apache2 license][apache2]. This is an initial version of the data modeling layer that will be used for defining API models in [Finch][finch].

See the following example to get an idea of what Booby is intended to do.

<script src="https://gist.github.com/4449143.js">
</script>

## Models should be data source independent

Although *resources definition* is one of the main Finch features, I've decided to release it as a separated project to keep these two parts as isolated as possible and that they can evolve independently. In the end, [data modeling][data_modeling] is a very important point in software design and development, and it should not be dependent of the data sources. Furthermore, the idea is that Finch will be completely independent of the resources definition layer sometime.

## Using Booby

During development I tried to keep Booby very simple for easy integration with other libraries and systems. Currently Booby is under active development and it is not a complete data modeling library yet, and [documentation][docs] isn't too complete, but I'm going to add new [field types][fields], [validators][validators] and serialization formats.

By the time, although there is so much work to do, you are encouraged to [install][install] and [try it][docs], report issues and contribute your code through [Github][github_repo].

[booby_02]: https://pypi.python.org/pypi/booby/0.2
[apache2]: https://www.apache.org/licenses/LICENSE-2.0.html
[finch]: https://www.jaimegil.me/2012/12/26/a-python-restful-api-consumer.html
[data_modeling]: https://en.wikipedia.org/wiki/Data_modeling
[docs]: https://booby.readthedocs.org
[fields]: https://booby.readthedocs.org/en/latest/fields.html
[validators]: https://booby.readthedocs.org/en/latest/validators.html
[install]: https://booby.readthedocs.org/en/latest/install.html
[github_repo]: https://github.com/jaimegildesagredo/booby
