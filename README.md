# AnotherEnum

`AnotherEnum` provides support for defining enumerated types in Ruby.  An enumerated type (or "enum") is a class with a finite (and usually small) set of predefined, named values.

## Usage

Define a enumerated type by subclassing AnotherEnum.  Use `.define` to define allowed values:

    require 'another_enum'

    class Colour < AnotherEnum
      define :red
      define :green
      define :blue
    end

which become globally available:

    Colour.red
    Colour.green
    Colour.blue

Each value gets a code:

    Colour.red.code     #=> "red"

which can be used later to lookup the value:

    Colour["red"]       #=> Colour.red

It's easy to get all the defined values, or all the codes:

    Colour.all          #=> [Colour.red, Colour.green, Colour.blue]
    Colour.codes        #=> ["red", "green", "blue"]

`AnotherEnum.define` takes a block, which can be used to define methods on the singleton values, e.g.

    class CreditCardType < AnotherEnum

      define :visa do

        def surcharge
          0.08
        end

      end

      define :amex do

        def surcharge
          0.16
        end

      end

    end

There's even a shortcut for defining methods that return predefined values:

    class CreditCardType < AnotherEnum

      define :visa do
        hardcode name: "Visa"
        hardcode surcharge: 0.08
      end

      define :amex do
        hardcode name: "American Express"
        hardcode surcharge: 0.16
      end

    end

## Contributing

It's on GitHub. You know what to do.
