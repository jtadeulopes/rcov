# RCov - Code Coverage for Ruby

## Why? What?

This is our fork of Mauricio Fernandez's RCov (maintained by [Relevance] [2]).

__NOTE:__ This fork __does not__ work on Ruby 1.9.x.  For coverage on Ruby 1.9 look at [SimpleCov] [3].

[![Build Status](https://secure.travis-ci.org/relevance/rcov.png?branch=master)](http://travis-ci.org/relevance/rcov)

## Install

    gem install rcov

## Bugs and Issues

[RCov Issues on GitHub] [1]

  [1]: http://github.com/relevance/rcov/issues/ "RCov Issues"
  [2]: http://thinkrelevance.com "Relevance"
  [3]: https://github.com/colszowka/simplecov

## More Info

rcov copyright (c) 2004-2012 Mauricio Fernandez <mfp@acm.org>
rcov copyright (c) 2008-2012 Aaron Bedra and Relevance Inc.

## rcov README

`Rcov` is a code coverage tool for `Ruby`. It is commonly used for viewing
overall test coverage of target code. It features:

* cross-referenced XHTML and several kinds of text reports
* support for easy automation with Rake
* colorblind-friendliness

## Requirements

* Ruby 1.8.6 or higher
* (recommended) C compiler: you can also use rcov without the rcovrt
  extension but rcov will be two orders of magnitude slower. The
  extension requires Ruby 1.8.6 or higher.

## Normal install

De-compress the archive and enter its top directory.
Then type:

	($ su)
	# ruby setup.rb

This simple step installs rcov under the default location for Ruby
libraries.  You can also customize the installation by supplying some
options to setup.rb.  Try `ruby setup.rb --help`.

A normal (rcovrt-enabled) install requires Ruby >= 1.8.6 and a working
C toolchain; if you cannot compile Ruby extensions proceed as
described below.

## Install without the rcovrt extension

	($su )
	# ruby setup.rb all --without-ext

will install rcov without building the rcovrt extension.

## Usage

In the common scenario, your tests are under `test/` and the target code
(whose coverage you want) is in `lib/`. In that case, all you have to do
is use rcov to run the tests (instead of testrb), and a number of
XHTML files with the code coverage information will be generated, e.g.

	rcov -Ilib test/*.rb

will execute all the `.rb` files under `test/` and generate the code
coverage report for the target code (i.e. for the files in `lib/`) under
`coverage/`. The target code needs not be under `lib/`; rcov will detect
is as long as it is `require`d by the tests. rcov is smart enough to
ignore "uninteresting" files: the tests themselves, files installed in
Ruby's standard locations, etc.  See `rcov --help` for the list of
regexps rcov matches filenames against.

rcov can also be used from `Rake`; see `doc/readme_for_rake` or the `RDoc`
documentation for more information.  The `Rakefile` included in rcov's
sources holds a few tasks that run rcov on itself, producing a number
of reports. You can try

	rake rcov

  preferably after a full install or

	ruby setup.rb config
	ruby setup.rb setup

so that the rcovrt extension can be used to speed up the process. This
will generate a cross-referenced XHTML report under `coverage/`.

rcov can output information in several formats, and perform different
kinds of analyses in addition to plain code coverage.  See `rcov --help`
for a description of the available options.

## License

rcov is licensed under the same terms as Ruby. See LICENSE.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are
met:

1. Redistributions of source code must retain the above copyright
   notice, this list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright
   notice, this list of conditions and the following disclaimer in the
   documentation and/or other materials provided with the distribution.
3. Neither the name of ePark Labs nor the names of its contributors
   may be used to endorse or promote products derived from this software
   without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
"AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
