# VS Code find and replace commands list

>> Note: all commands work in find box for that use ctrl + f to open find box
>> In find box have find and replace options
>> On find box also have 3 options by which find different type of parametters on code
>> 1. Match case
>> 1. Match whole word
>> 1. Use regular expression

## Remove new lines form code in vs code

Select only `use regular expression` then on find box type `^\n` then in replace do nothing and `replace all`


## Remove dublicate line when dublicate linse are side by side other wise its not work in vs code

Select only `use regular expression` find -> `^(.*)(\n\1)+$` replace -> `$1`

## Remove dublicate line form code using extention 

Download `Transformer` extention by `dakara`
Open `command platter` type -> `Trime Trailing Widespace`

## Remove space form code in vs code

On `command pallater ctrl + shift + p` and find `trim traillig whidespace` will remove all whidespace