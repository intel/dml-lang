<!--
  © 2021-2022 Intel Corporation
  SPDX-License-Identifier: MPL-2.0
-->
The following sections list the warnings and error messages from
`dmlc`, with some clarifications.

## Warning Messages

The messages are listed in alphabetical order; the corresponding tags
are shown within brackets, e.g., `[WNDOC]`.

<dl>
  <dt><b>

... [WSYSTEMC]</b></dt>
  <dd>

SystemC specific warnings
</dd>
  <dt><b>

... [WWRNSTMT]</b></dt>
  <dd>

The source code contained a statement "`warning;`", which
causes a warning to be printed.
</dd>
  <dt><b>

'X then Y' log level has no effect when the levels are the same [WREDUNDANTLEVEL]</b></dt>
  <dd>

`X then Y` log level syntax has no effect when the
first and subsequent levels are the same.
</dd>
  <dt><b>

Comparing negative constant to unsigned integer has a constant result [WNEGCONSTCOMP]</b></dt>
  <dd>

DML uses a special method when comparing an unsigned and signed integer,
meaning that comparing a negative constant to an unsigned integer always
has the same result, which is usually not the intended behaviour.
</dd>
  <dt><b>

Outdated AST file: ... [WOLDAST]</b></dt>
  <dd>

A precompiled DML file has an old time-stamp. This may happen if a
user accidentally edits a DML file from the standard library. A
safe way to suppress the warning is to remove the outdated
`.dmlast` file.
</dd>
  <dt><b>

The assignment source is a constant value which does not fit the assign target of type '...', and will thus be truncated [WASTRUNC]</b></dt>
  <dd>

The source of an assignment is a constant value that can't fit in the
type of the target, and is thus truncated. This warning can be silenced by
explicitly casting the expression to the target type.
</dd>
  <dt><b>

Use of unsupported feature: ... [WEXPERIMENTAL]</b></dt>
  <dd>

This part of the language is experimental, and not yet officially
supported. Code relying on the feature may break without notice in
future releases.
</dd>
  <dt><b>

Use of unsupported feature: ... [WEXPERIMENTAL_UNMAPPED]</b></dt>
  <dd>

This part of the language is experimental, and not yet officially
supported. Code relying on the feature may break without notice in
future releases.
</dd>
  <dt><b>

deprecation: ... [WDEPRECATED]</b></dt>
  <dd>

This part of the language is deprecated, usually because the
underlying support in Simics is deprecated.
</dd>
  <dt><b>

duplicate event checkpoint names: ... [WDUPEVENT]</b></dt>
  <dd>

Two or more events will be checkpointed using the same name, which
means that the checkpoint cannot be safely read back.
</dd>
  <dt><b>

file has no version tag, assuming version 1.2 [WNOVER]</b></dt>
  <dd>

A DML file must start with a version statement, such as `dml 1.2;`
</dd>
  <dt><b>

implementation of ...() without 'is ...' is ignored by the standard library [WNOIS]</b></dt>
  <dd>

Many standard method overrides will only be recognized if a
template named like the method is also instantiated. For instance,
the method `set` in a field has no effect unless the
`set` template is instantiated.
</dd>
  <dt><b>

negative register offset: <i>N</i> [WNEGOFFS]</b></dt>
  <dd>

A negative integer expression is given as a register offset.
Register offsets are unsigned 64-bit numbers, which means that
a negative offset expression translates to a very large offset.
</dd>
  <dt><b>

no 'desc' parameter specified for device [WNSHORTDESC]</b></dt>
  <dd>

No short description string was specified using the 'desc' parameter.
(This warning is disabled by default.)
</dd>
  <dt><b>

no documentation for '...' [WNDOC]</b></dt>
  <dd>

No documentation string was specified for the attribute.
(This warning is disabled by default.)
</dd>
  <dt><b>

no documentation for required attribute '...' [WNDOCRA]</b></dt>
  <dd>

No documentation string was specified for a _required_ attribute.
</dd>
  <dt><b>

overriding non-throwing DML 1.4 method with throwing DML 1.2 method [WTHROWS_DML12]</b></dt>
  <dd>

In DML 1.2, a method is by default permitted to throw an exception,
while in DML 1.4, an annotation `throws` is required for that.
So, if a method without annotations is ported to DML 1.4, it will
no longer permit exceptions. If such method is overridden by
a DML 1.2 file, then a non-throwing method is overridden by a potentially
throwing method, which is normally a type error. However, this particular
case is reduced to this warning. If an exception is uncaught in the
override, then this will automatically be caught in runtime and
an error message will be printed.
</dd>
  <dt><b>

potential leak of confidential information [WCONFIDENTIAL]</b></dt>
  <dd>

The object's name/qname is used as part of an expression in a
context other than the log statement, which could potentially lead
to the leak of confidential information.
</dd>
  <dt><b>

prefer 'is' statement outside template braces, 'template ... is (x, y) {' [WTEMPLATEIS]</b></dt>
  <dd>

In a template with methods marked `shared`, it is recommended that
other templates are instantiated on the same line
</dd>
  <dt><b>

shifting away all data [WSHALL]</b></dt>
  <dd>

The result of the shift operation will always be zero.
(This warning is disabled by default.)
</dd>
  <dt><b>

sizeof on a type is not legal, use sizeoftype instead [WSIZEOFTYPE]</b></dt>
  <dd>

The 'sizeof' operator is used on a type name, but expects an
expression. Use the 'sizeoftype' operator for types.
</dd>
  <dt><b>

the time value of type '...' is implicitly converted to the type '...' expected by the specified time unit '...'. [WTTYPEC]</b></dt>
  <dd>

The delay value provided to an `after` call is subject to
implicit type conversion which may be unexpected for certain types.
To silence this warning, explicitly cast the delay value to the expected
type.
</dd>
  <dt><b>

unused implementation of DML 1.2 method ...; enclose in #if (dml_1_2) ? [WUNUSED_DML12]</b></dt>
  <dd>

A DML 1.4 file contains a method implementation that would override
a library method in DML 1.2, but which is not part of the DML 1.4
library, because some methods have been renamed. For instance,
implementing `read_access` in a register makes no sense
in DML 1.4, because the method has been renamed to
`read_register`.

If a DML 1.4 file contains common code that also is imported from
DML 1.2 devices, then it may need to implement methods like
`read_access` to get the right callbacks when compiled
for DML 1.2. Such implementations can be placed inside `#if
(dml_1_2) { }` blocks to avoid this warning.
</dd>
  <dt><b>

unused parameter ... contains ... [WREF]</b></dt>
  <dd>

An unused parameter refers to an object that has not been declared.

This warning message will be replaced with a hard error in future
major versions of Simics.
</dd>
  <dt><b>

unused: ... [WUNUSED]</b></dt>
  <dd>

The object is not referenced anywhere.
(This warning is disabled by default.; it typically causes many false
warnings.)
</dd>
  <dt><b>

unused: ... methods are not called automatically for ... objects in ... [WUNUSEDDEFAULT]</b></dt>
  <dd>

The object is not referenced anywhere but it matches a name of an
object automatically referenced in another scope. This is the same
as WUNUSED but only for known common errors and it will never be
emitted if WUNUSED is enabled.
</dd>
</dl>


## Error Messages

The messages are listed in alphabetical order; the corresponding tags
are shown within brackets, e.g., `[ENBOOL]`.

<dl>
  <dt><b>

... [EERRSTMT]</b></dt>
  <dd>

The source code contained a statement "`error;`", which
forces a compilation error with the given message, or the standard message
"forced compilation error in source code".
</dd>
  <dt><b>

... in template ... does not belong to the template type [ENSHARED]</b></dt>
  <dd>

If a template provides an object that is not accessible from shared
methods, such as an untyped parameter or a non-shared method, then
that object's name is reserved within the scope of the shared
method.  I.e., if a shared method tries to access a symbol that
isn't accessible, then ENSHARED is reported, even before looking
for the symbol in the global scope. Section
[x](3.-Device-Modeling-Language,-version-1.4#shared-methods) describes which template symbols
are accessible from a shared method.
</dd>
  <dt><b>

'...' has no member named '...' [EMEMBER]</b></dt>
  <dd>

Attempt to access a nonexisting member of a compound data structure.
</dd>
  <dt><b>

'.len' cannot be used with variable-length arrays [EVLALEN]</b></dt>
  <dd>

<tt>.len</tt> cannot be used with variable-length arrays
</dd>
  <dt><b>

Ambiguous invocation of default implementation [EAMBDEFAULT]</b></dt>
  <dd>

A method may not invoke its default implementation if multiple
methods are overridden, and the template inheritance graph is
insufficient to infer that one default implementation overrides
the others. See section [x](3.-Device-Modeling-Language,-version-1.4#calling-methods) for details.
</dd>
  <dt><b>

Cannot declare '...' variable in an inline method [ESTOREDINLINE]</b></dt>
  <dd>

You cannot declare session or saved variables in methods marked with
'inline'
</dd>
  <dt><b>

DML version ... does not support API version ... [ESIMAPI]</b></dt>
  <dd>

The DML file is written in a too old version of DML. Use the
`--simics-api` option to use a sufficiently old Simics API.
</dd>
  <dt><b>

Declaration would result in conflicting attribute name [EATTRCOLL]</b></dt>
  <dd>

This error is signalled if two DML declarations would result in two
Simics attributes being registered with the same name.

This most commonly happens when an attribute name is a result of the
object hierarchy, and there is another object named similarly. For example,
if a bank contains one register named `g_r` and
a group `g` containing a register named `r`.
</dd>
  <dt><b>

Instantiating template ... requires abstract ... ... to be implemented [EABSTEMPLATE]</b></dt>
  <dd>

If a template has any abstract methods or parameters, they must all be
implemented when instantiating the template.
</dd>
  <dt><b>

abstract method ... overrides existing method [EAMETH]</b></dt>
  <dd>

An abstract method cannot override another method.
</dd>
  <dt><b>

an anonymous ... cannot implement interfaces [EANONPORT]</b></dt>
  <dd>

An `implement` definition can only exist in a port or bank
that has a name.
</dd>
  <dt><b>

array index out of bounds [EOOB]</b></dt>
  <dd>

The used index is outside the defined range.
</dd>
  <dt><b>

array range must start at 0 [EZRANGE]</b></dt>
  <dd>

An array index range must start at zero.
</dd>
  <dt><b>

array size is less than 1 [EASZR]</b></dt>
  <dd>

An array must have at least one element.
</dd>
  <dt><b>

array upper bound is not a constant integer: ... [EASZVAR]</b></dt>
  <dd>

The size of an array must be a constant integer.
</dd>
  <dt><b>

assignment to constant [ECONST]</b></dt>
  <dd>

The lvalue that is assigned to is declared as a `const` and
thus can't be assigned to.
</dd>
  <dt><b>

attempt to override non-default method '...' [EDMETH]</b></dt>
  <dd>

A method can only be overridden if it is declared as `default`
</dd>
  <dt><b>

attempt to override non-shared method ... with shared method [ETMETH]</b></dt>
  <dd>

A shared method cannot override a non-shared method
</dd>
  <dt><b>

attribute has no get or set method [EANULL]</b></dt>
  <dd>

An attribute must have a set or a get method to be useful.
</dd>
  <dt><b>

attribute type undefined: ... [EATYPE]</b></dt>
  <dd>

Either the `attr_type` or the `type` parameter of the
attribute must be specified.
</dd>
  <dt><b>

bad declaration of automatic parameter '...' [EAUTOPARAM]</b></dt>
  <dd>

Some parameters are predefined by DML, using the `auto`
keyword. Such parameters may only be declared by the standard
library, and they may not be overridden.
</dd>
  <dt><b>

bit range of field '...' outside register boundaries [EBITRR]</b></dt>
  <dd>

The bit range of a field can only use bits present in the
register.
</dd>
  <dt><b>

bit range of field '...' overlaps with field '...' [EBITRO]</b></dt>
  <dd>

The fields of a register must not overlap.
</dd>
  <dt><b>

bitslice size of ... bits is not between 1 and 64 [EBSSIZE]</b></dt>
  <dd>

Bit slices cannot be larger than 64 bits.
</dd>
  <dt><b>

bitslice with big-endian bit order and uncertain bit width [EBSBE]</b></dt>
  <dd>

A big-endian bit slice can only be done on an expression whose type
is explicitly defined, such as a local variable or a register field.
</dd>
  <dt><b>

cannot assign to inlined parameter: '...' [EASSINL]</b></dt>
  <dd>

The target of the assignment is a method parameter that has been
given a constant or undefined value when inlining the method.
</dd>
  <dt><b>

cannot assign to this expression: '...' [EASSIGN]</b></dt>
  <dd>

The target of the assignment is not an l-value, and thus cannot be
assigned to.
</dd>
  <dt><b>

cannot declare a multi-dimensional ... in simics 5 [EMDOBJECT]</b></dt>
  <dd>

Bank arrays and port arrays cannot be multi-dimensional in simics 5
</dd>
  <dt><b>

cannot define both 'allocate_type' parameter and local data objects [EATTRDATA]</b></dt>
  <dd>

Specifying `allocate_type` and using 'data'
declarations in the same attribute object is not allowed.
</dd>
  <dt><b>

cannot export this method [EEXPORT]</b></dt>
  <dd>

Can only export non-inline, non-shared, non-throwing methods declared
outside object arrays.
</dd>
  <dt><b>

cannot find file to import: ... [EIMPORT]</b></dt>
  <dd>

The file to imported could not be found. Use the `-I`
option to specify additional directories to search for imported
files.
</dd>
  <dt><b>

cannot import file containing device declaration [EDEVIMP]</b></dt>
  <dd>

Source files that are used with `import` directives may not
contain `device` declarations.
</dd>
  <dt><b>

cannot use a register with fields as a value: ... [EREGVAL]</b></dt>
  <dd>

When a register has been specified with explicit fields, you have to
use the `get` and `set` methods to access the register as
a single value.
</dd>
  <dt><b>

cannot use an array as a value: '...' [EARRAY]</b></dt>
  <dd>

A whole array cannot be used as a single value.
</dd>
  <dt><b>

cannot use endian integer as argument type in declaration [EEARG]</b></dt>
  <dd>

Function and method arguments in declarations cannot be of
endian integer type.
</dd>
  <dt><b>

cannot use variable index in a constant list [EAVAR]</b></dt>
  <dd>

Indexing into constant lists can only be done with constant indexes.
</dd>
  <dt><b>

checkpointable attribute missing set or get method [EACHK]</b></dt>
  <dd>

An attribute must have set and get methods to be
checkpointable. This attribute has neither, and the
'configuration' parameter is either "required" or "optional".
</dd>
  <dt><b>

circular dependency in parameter value [ERECPARAM]</b></dt>
  <dd>

The value of a parameter may not reference the parameter itself,
neither directly nor indirectly.
</dd>
  <dt><b>

conditional 'in each' is not allowed [ECONDINEACH]</b></dt>
  <dd>

It is not permitted to have an `in each` statement directly
inside an `if` conditional.
</dd>
  <dt><b>

conditional parameters are not allowed [ECONDP]</b></dt>
  <dd>

It is not permitted to declare a parameter directly inside an
`if` conditional.
</dd>
  <dt><b>

conditional templates are not allowed [ECONDT]</b></dt>
  <dd>

It is not permitted to use a template directly inside an
`if` conditional.
</dd>
  <dt><b>

conflicting default definitions for method '...' [EDDEFMETH]</b></dt>
  <dd>

If a method has two default implementations, then at least one
of them must be defined in a template.
</dd>
  <dt><b>

conflicting definitions of ... when instantiating ... and ... [EAMBINH]</b></dt>
  <dd>

If a method or parameter has multiple definitions, then there must
be a unique definition that overrides all other definitions.
</dd>
  <dt><b>

const qualifier discarded [EDISCONST]</b></dt>
  <dd>

A pointer to a constant value has been assigned to a pointer to a
non-constant.
</dd>
  <dt><b>

continue is not possible here [ECONTU]</b></dt>
  <dd>

A `continue` statement cannot be used in a `foreach`
or `select` statement.
</dd>
  <dt><b>

cyclic import [ECYCLICIMP]</b></dt>
  <dd>

A DML file imports itself, either directly or indirectly.
</dd>
  <dt><b>

cyclic template inheritance [ECYCLICTEMPLATE]</b></dt>
  <dd>

A template inherits from itself, either directly or indirectly.
</dd>
  <dt><b>

duplicate bank function number: <i>N</i> [EDBFUNC]</b></dt>
  <dd>

The device contains two differently-named banks that use the same
function number.
</dd>
  <dt><b>

duplicate definition of variable '...' [EDVAR]</b></dt>
  <dd>

A local variable has more than one definition in the same code block.
</dd>
  <dt><b>

duplicate method parameter name '...' [EARGD]</b></dt>
  <dd>

All parameter names of a method must be distinct.
</dd>
  <dt><b>

expression may not depend on the index variable ... [EIDXVAR]</b></dt>
  <dd>

Expressions that are evaluated statically to constants cannot have
different values for different elements in a register array.  This
includes, for instance, the `allocate` parameter in
registers and fields, and object-level `if` statements.
</dd>
  <dt><b>

file not found [ENOFILE]</b></dt>
  <dd>

The main input file could not be found.
</dd>
  <dt><b>

heterogeneous bitsize in field array [EFARRSZ]</b></dt>
  <dd>

The bit width must be identical across the elements of a field array.
</dd>
  <dt><b>

illegal 'after' call to '...': ... [EAFTER]</b></dt>
  <dd>

An illegal `after (..) call ..` was made.  A method called this way
may only have serializable input parameters, and may not have any output
parameters.
</dd>
  <dt><b>

illegal attribute name: ... [EANAME]</b></dt>
  <dd>

This name is not available as the name of an attribute, since it is
used for an automatically added attribute.
</dd>
  <dt><b>

illegal bitfields definition: ... [EBFLD]</b></dt>
  <dd>

A `bitfield` declaration must have an integer type that
matches the width of the field.
</dd>
  <dt><b>

illegal bitorder: '...' [EBITO]</b></dt>
  <dd>

The specified bit-order is not allowed.
</dd>
  <dt><b>

illegal bitslice operation [EBSLICE]</b></dt>
  <dd>

A bitslice operation was attempted on an expression that is not an
integer.
</dd>
  <dt><b>

illegal cast to '...' [ECAST]</b></dt>
  <dd>

The cast operation was not allowed.  It is illegal to cast to void.
</dd>
  <dt><b>

illegal comparison; mismatching types [EILLCOMP]</b></dt>
  <dd>

The values being compared do not have matching types.
</dd>
  <dt><b>

illegal function application of '...' [EAPPLY]</b></dt>
  <dd>

The applied value is not a function.
</dd>
  <dt><b>

illegal increment/decrement operation [EINC]</b></dt>
  <dd>

An increment or decrement operation can only be performed on simple
lvalues such as variables.
</dd>
  <dt><b>

illegal interface method reference: ... [EIFREF]</b></dt>
  <dd>

Interface function calls must be simple references to the method.
</dd>
  <dt><b>

illegal layout definition: ... [ELAYOUT]</b></dt>
  <dd>

The type of a member of a `layout` declaration must be an integer or
bitfield with a bit width that is a multiple of 8, or another layout.
</dd>
  <dt><b>

illegal operands to binary '...'  [EBINOP]</b></dt>
  <dd>

One or both of the operands have the wrong type for the given binary
operator.
</dd>
  <dt><b>

illegal pointer type: ... [EINTPTRTYPE]</b></dt>
  <dd>

Pointer types that point to integers with a bit width that is not
a power of two are not allowed.
</dd>
  <dt><b>

illegal register size for '...' [EREGISZ]</b></dt>
  <dd>

The specified register size is not allowed. Possible values are 1-8.
</dd>
  <dt><b>

illegal use of void type [EVOID]</b></dt>
  <dd>

The type `void` is not a value, and thus cannot be used as
the type of e.g. a variable or struct member
</dd>
  <dt><b>

illegal value for parameter '...' [EPARAM]</b></dt>
  <dd>

The parameter is not bound to a legal value.
</dd>
  <dt><b>

incompatible array declarations: ... [EAINCOMP]</b></dt>
  <dd>

The array has been declared more than once, in an incompatible way.
</dd>
  <dt><b>

incompatible method definitions: ... [EMETH]</b></dt>
  <dd>

The default implementation is overridden by an implementation with
different input/output parameters.
</dd>
  <dt><b>

incompatible version (...) while compiling a ... device [EVERS]</b></dt>
  <dd>

A device declared to be written in one DML language version tried to
import a file written in an incompatible language version.
</dd>
  <dt><b>

invalid data initializer: ... [EDATAINIT]</b></dt>
  <dd>

An invalid initializer was detected. The error message provides
the detailed information.
</dd>
  <dt><b>

invalid expression: '...' [EINVALID]</b></dt>
  <dd>

The expression does not produce a proper value.
</dd>
  <dt><b>

invalid log type: '...' [ELTYPE]</b></dt>
  <dd>

Log-statement type must be one of `info`, `error`,
`spec_viol`, and `unimpl`.
</dd>
  <dt><b>

invalid name parameter value: '...' [ENAMEID]</b></dt>
  <dd>

The name parameter does not follow identifier syntax.
</dd>
  <dt><b>

invalid override of non-default declaration ... [EINVOVER]</b></dt>
  <dd>

Only default declarations of parameters can be overridden.
</dd>
  <dt><b>

invalid upcast, ... not a subtemplate of ... [ETEMPLATEUPCAST]</b></dt>
  <dd>

When casting to a template type, the source expression must be either
an object implementing the template, or an expression whose type is a
subtemplate of the target type.
</dd>
  <dt><b>

log level must be an integer between 1 and <i>N</i> [ELLEV]</b></dt>
  <dd>

The log level given in a log statement must be an integer between 1 and 4.
Or 1 and 5 for a subsequent log level (`then ...`).
</dd>
  <dt><b>

malformed format string: unknown format at position <i>N</i> [EFORMAT]</b></dt>
  <dd>

The log-statement format string is malformed.
</dd>
  <dt><b>

malformed switch statement: ... [ESWITCH]</b></dt>
  <dd>

A switch statement must start with a `case` label, and there
may be at most one `default` label which must appear after
all `case` labels
</dd>
  <dt><b>

method return type declarations may not be named: ... [ERETARGNAME]</b></dt>
  <dd>

In DML 1.4, the output arguments of a method are anonymous
</dd>
  <dt><b>

missing device declaration [EDEVICE]</b></dt>
  <dd>

The main source file given to the DML compiler must contain a
`device` declaration.
</dd>
  <dt><b>

missing return statement in method with output argument [ENORET]</b></dt>
  <dd>

If a method has output arguments, then control flow may not reach
the end of the method. Either an explicit value must be returned
in a return statement, or the execution must be aborted by an
exception or assertion failure. Note that DMLC's control flow
analysis is rather rudimentary, and can issue this error on code
that provably will return. In this case, the error message can be
silenced by adding `assert false;` to the end of the
method body.
</dd>
  <dt><b>

more than one output parameter not allowed in interface methods [EIMPRET]</b></dt>
  <dd>

Methods within an `interface` declaration may have only have
zero or one output parameter.
</dd>
  <dt><b>

name collision on '...' [ENAMECOLL]</b></dt>
  <dd>

The name is already in use in the same scope.
</dd>
  <dt><b>

negative size (<i>N</i> &lt; <i>N</i>) of bit range for '...' [EBITRN]</b></dt>
  <dd>

The size of the bit range must be positive. Note that the [msb:lsb]
syntax requires that the most significant bit (msb) is written to the
left of the colon, regardless of the actual bit numbering used.
</dd>
  <dt><b>

no assignment to parameter '...' [ENPARAM]</b></dt>
  <dd>

The parameter has been declared, but is not assigned a value or a
default value.
</dd>
  <dt><b>

no default implementation [ENDEFAULT]</b></dt>
  <dd>

The default implementation of a method was invoked, but there was
no default implementation.
</dd>
  <dt><b>

no return type [ERETTYPE]</b></dt>
  <dd>

The type of the return value (if any) must be specified for methods
that implement interfaces.
</dd>
  <dt><b>

no type for ... parameter '...' [ENARGT]</b></dt>
  <dd>

Methods that are called must have data type declarations for all
their parameters. (Methods that are only inlined do not need this.)
</dd>
  <dt><b>

non-boolean condition: '...' of type '...' [ENBOOL]</b></dt>
  <dd>

Conditions must be properly boolean expressions; e.g., "`if (i ==
0)`" is allowed, but "`if (i)`" is not, if `i` is an
integer.
</dd>
  <dt><b>

non-constant element in list [ECLST]</b></dt>
  <dd>

Lists may only contain constants.
</dd>
  <dt><b>

non-constant expression: ... [ENCONST]</b></dt>
  <dd>

A constant expression was expected.
</dd>
  <dt><b>

non-constant parameter, or circular parameter dependencies: '...' [EVARPARAM]</b></dt>
  <dd>

The value assigned to the parameter is not a well-defined constant.
</dd>
  <dt><b>

non-constant strings cannot be concatenated using '+' [ECSADD]</b></dt>
  <dd>

Non-constant strings cannot be concatenated using `+`.
</dd>
  <dt><b>

not a list: ... [ENLST]</b></dt>
  <dd>

A list was expected.
</dd>
  <dt><b>

not a method: '...' [ENMETH]</b></dt>
  <dd>

A method name was expected. This might be caused by using
`call` or `inline` on something that counts as a C
function rather than a method.
</dd>
  <dt><b>

not a pointer: ... (...) [ENOPTR]</b></dt>
  <dd>

A pointer value was expected.
</dd>
  <dt><b>

not a value: ... [ENVAL]</b></dt>
  <dd>

Only some objects can be used as values directly. An attribute can
only be accessed directly as a value if it has been declared using the
`allocate_type` parameter.
</dd>
  <dt><b>

nothing to break from [EBREAK]</b></dt>
  <dd>

A `break` statement can only be used inside a loop or switch
construct.
</dd>
  <dt><b>

nothing to continue [ECONT]</b></dt>
  <dd>

A `continue` statement can only be used inside a loop construct.
</dd>
  <dt><b>

object expected: ... [ENOBJ]</b></dt>
  <dd>

A reference to an object was expected.
</dd>
  <dt><b>

object is not allocated at run-time: ... [ENALLOC]</b></dt>
  <dd>

An object which is not allocated at run-time cannot be referenced as
a run-time value.
</dd>
  <dt><b>

operand of '...' is not an lvalue [ERVAL]</b></dt>
  <dd>

The operand of `sizeof`, `typeof` and `&` must
be a lvalue.
</dd>
  <dt><b>

overlapping registers: '...' and '...' [EREGOL]</b></dt>
  <dd>

The registers are mapped to overlapping address ranges.
</dd>
  <dt><b>

passing const reference for nonconst parameter ... in ... [ECONSTP]</b></dt>
  <dd>

C function called with a pointer to a constant value for a parameter
declared without const in the prototype.
</dd>
  <dt><b>

recursive inline of ... [ERECUR]</b></dt>
  <dd>

Methods may not be inlined recursively.
</dd>
  <dt><b>

recursive type definition of ... [ETREC]</b></dt>
  <dd>

The definition of a structure type can not have itself as direct or
indirect member.
</dd>
  <dt><b>

reference to unknown object '...' [EREF]</b></dt>
  <dd>

The referenced object has not been declared.
</dd>
  <dt><b>

right-hand side operand of '...' is zero [EDIVZ]</b></dt>
  <dd>

The right-hand side of the given / or % operator is always zero.
</dd>
  <dt><b>

saved variable declared with (partially) const-qualified type ... [ESAVEDCONST]</b></dt>
  <dd>

Declaring a saved variable with a type that is (partially) const-qualified
is not allowed, as they can be modified due to checkpoint restoration.
</dd>
  <dt><b>

shift with negative shift count: '... [ESHNEG]</b></dt>
  <dd>

The right-hand side operand to a shift operator must not be negative.
</dd>
  <dt><b>

struct declaration not allowed in a ... [EANONSTRUCT]</b></dt>
  <dd>

Declarations of new structs are not permitted in certain contexts,
such as method arguments, `new` expressions,
`sizeoftype` expressions and `cast` expressions.
</dd>
  <dt><b>

struct or layout with no fields [EEMPTYSTRUCT]</b></dt>
  <dd>

A struct or layout type must have at least one field.
This restriction does not apply to structs declared in a
`extern typedef`.
</dd>
  <dt><b>

syntax error...... [ESYNTAX]</b></dt>
  <dd>

The code is malformed.
</dd>
  <dt><b>

the size of dimension <i>N</i> (with index variable '...') is never defined [EAUNKDIMSIZE]</b></dt>
  <dd>

The size of an array dimension of an object array must be defined at least
once across all declarations of that object array.
</dd>
  <dt><b>

this object is not allowed here [ENALLOW]</b></dt>
  <dd>

Many object types have limitations on the contexts in which they may
appear.
</dd>
  <dt><b>

trying to get a member of a non-struct: '...' of type '...' [ENOSTRUCT]</b></dt>
  <dd>

The left-hand side operand of the `.` operator is not of struct
type.
</dd>
  <dt><b>

trying to index something that isn't an array: '...' [ENARRAY]</b></dt>
  <dd>

Indexing can only be applied to arrays, integers (bit-slicing),
and lists.
</dd>
  <dt><b>

uncaught exception [EBADFAIL]</b></dt>
  <dd>

An exception is thrown in a context where it will not be caught.
</dd>
  <dt><b>

uncaught exception in call to DML 1.2 method '...' [EBADFAIL_dml12]</b></dt>
  <dd>

If a DML 1.2 method lacks a `nothrow` annotation, and a
non-throwing DML 1.4 method calls it, then DMLC will analyze
whether the method call can actually cause an exception. If it
can, this error is reported; if not, the call is permitted.

For this error, a 1.2 method counts as throwing if it throws an
exception, or calls a `throws` marked 1.4 method, or
(recursively) if it invokes a method that counts as throwing. A
call or throw statement inside a `try` block does not cause
the method to count as throwing. The methods
`attribute.set`, `bank.read_access` and
`bank.write_access` count as throwing even if they don't
throw.

This error is normally reported while porting common DML 1.2 code
to DML 1.4: most 1.2 methods are not meant to throw exceptions,
and when converted to DML 1.4 this becomes a strict requirement
unless the method is annotated with the `throws` keyword.
The remedy for this error message is normally to insert a
`try` block around some call along the throwing call chain,
with a `catch` block that handles the exception
gracefully. The `try` block should usually be as close as
possible to the `throw` in the call chain.
</dd>
  <dt><b>

undefined register size for '...' [EREGNSZ]</b></dt>
  <dd>

All registers must have a specified constant size.
</dd>
  <dt><b>

undefined value: '...' [EUNDEF]</b></dt>
  <dd>

Caused by an attempt to generate code for an expression that
contains the `undefined` value.
</dd>
  <dt><b>

unknown identifier: '...' [EIDENT]</b></dt>
  <dd>

The identifier has not been declared anywhere.
</dd>
  <dt><b>

unknown interface type: ... [EIFTYPE]</b></dt>
  <dd>

The interface datatype is unknown.
</dd>
  <dt><b>

unknown template: '...' [ENTMPL]</b></dt>
  <dd>

The template has not been defined.
</dd>
  <dt><b>

unknown type of expression [ENTYPE]</b></dt>
  <dd>

This expression has an unknown type.
</dd>
  <dt><b>

unknown type: '...' [ETYPE]</b></dt>
  <dd>

The data type is not defined in the DML code.
</dd>
  <dt><b>

unserializable type: ... [ESERIALIZE]</b></dt>
  <dd>

Some complex types, in particular most pointer types, cannot be
automatically checkpointed by DML, and are therefore disallowed in
contexts such as `saved` declarations.
</dd>
  <dt><b>

value of parameter ... is not yet initialized [EUNINITIALIZED]</b></dt>
  <dd>

Some parameters that are automatically supplied by DML
cannot be accessed in early stages of compilation, such as in object-level
if statements.
</dd>
  <dt><b>

variable length array declared with (partially) const-qualified type [EVLACONST]</b></dt>
  <dd>

Variable length arrays may not be declared const-qualified or with a base
type that is (partially) const-qualified.
</dd>
  <dt><b>

variable or field declared ... [EVARTYPE]</b></dt>
  <dd>

A variable has been declared with a given type but the type is
not acceptable.
</dd>
  <dt><b>

wrong number of ... arguments [EARG]</b></dt>
  <dd>

The number of input/output arguments given in the call differs from
the method definition.
</dd>
  <dt><b>

wrong number of arguments for format string [EFMTARGN]</b></dt>
  <dd>

The log-statement has too few or too many arguments for the given
format string.
</dd>
  <dt><b>

wrong number of return value recipients: Expected <i>N</i>, got <i>N</i> [ERETLVALS]</b></dt>
  <dd>

The number of return value recipients differs from the number of values
the called method returns.
</dd>
  <dt><b>

wrong number of return values: Expected <i>N</i>, got <i>N</i> [ERETARGS]</b></dt>
  <dd>

The number of return values in a return statement must match the number
of outputs in the method.
</dd>
  <dt><b>

wrong type [EBTYPE]</b></dt>
  <dd>

An expression had the wrong type.
</dd>
  <dt><b>

wrong type for '...' operator [EINCTYPE]</b></dt>
  <dd>

The prefix and postfix increment/decrement operators can only be
used on integer and pointer expressions.
</dd>
  <dt><b>

wrong type for argument <i>N</i> of format string ('...') [EFMTARGT]</b></dt>
  <dd>

Argument type mismatch in a log-statement format string.
</dd>
  <dt><b>

wrong type for parameter ... in ... call [EPTYPE]</b></dt>
  <dd>

The data type of the argument value given for the mentioned
method or function parameter differs from the function prototype.
</dd>
  <dt><b>

wrong type in ... parameter '...' when ... '...' [EARGT]</b></dt>
  <dd>

The data type of the argument value given for the mentioned method
parameter differs from the method definition.
</dd>
  <dt><b>

wrong type in assignment [EASTYPE]</b></dt>
  <dd>

The target of an assignment can't store the value given in the
source, because they are of different types.
</dd>
</dl>
