<!--
  © 2021-2022 Intel Corporation
  SPDX-License-Identifier: MPL-2.0
-->
<dl>
  <dt>PABSTRACT_TEMPLATE</dt>
  <dd>

When implementing methods `read` or `write` in a
field or register, or `hard_reset` or
`soft_reset` in a bank, or `get`, `set`,
`read_field`, `write_field` in a field, then this will
have no effect unless a template named like the method is instantiated. The
automatic converter will add e.g. `is read;` before an
implementation of `read`.
</dd>
  <dt>PAFTER</dt>
  <dd>

The syntax of `after` statements changed: The delay should
be followed by `s` to denote time unit; furthermore, the
`call` keyword should no longer be used, and brackets
around the delay are optional. Example:
```
after (1.3) call send_frame();  // DML 1.2 syntax
after 1.3 s: send_frame();       // DML 1.4 syntax
```
</dd>
  <dt>PANDOR</dt>
  <dd>

DML 1.2 permits the right operand of an `&&` or
`||` expression to contain errors, as long as the left
operand evaluates to a constant that makes the right operand
dead. DML 1.4 does not permit this, so the expression `A
&& B` must be converted to `A #? B #: false`.
One common use case is expressions like
`(defined X && X.y == ...)`.
</dd>
  <dt>PARRAY</dt>
  <dd>

The syntax for object arrays has changed: Instead of
`register r[j in 0..size - 1]`, you write
`register r[j < size]`
</dd>
  <dt>PARRAY_I</dt>
  <dd>

The syntax for object arrays has changed: Instead of
`register r[12]`, you write `register r[i < 12]`
</dd>
  <dt>PATTRIBUTE</dt>
  <dd>

The `allocate_type` parameter is no longer valid for attributes.
Integer, boolean and floating-point attributes instead use
standard templates such as `uint64_attr`, `int64_attr`, `bool_attr` and
`double_attr`.

The porting rule will remove `allocate_type`, together with an
explicit type parameter if present. All integer types will be
changed to 64-bit types. Attributes with `allocate_type="string"`
have to be manually rewritten.
</dd>
  <dt>PAUTO</dt>
  <dd>

The `auto` keyword is deprecated; use the equivalent
`local` instead.
</dd>
  <dt>PBEFAFT</dt>
  <dd>

In objects of type attribute, register and connect, before/after
methods (e.g. `before_write`, `after_read`,
`after_set`), are no longer called. They are transformed
into an override of the corresponding base function
(`write_register`, `read_register`, `set`).
Note that when a before/after method is implemented by a template,
then an additional `is register` declaration may be needed in
1.4; this is not automatically added.
</dd>
  <dt>PBITNEQ</dt>
  <dd>

DML 1.2 permits using 1-bit fields as boolean values. In DML 1.4,
field values are 64 bit, and thus require an explicit `!= 0`
</dd>
  <dt>PCHANGE_INARGS</dt>
  <dd>

Many overridable methods in the standard library have changed, and
method overrides must be changed accordingly. A method in 1.2
usually has a counterpart in 1.4, but its semantics may have
changed slightly and quite often the set of arguments has changed
as well.  The automatic converter will adjust the names and
signatures of a number of methods. Invocations, including
`default()`, are not updated and must be manually converted
(compile errors). Some method arguments are removed by the
converter; if these arguments are used, the implementation must be
modified accordingly. In particular, the `memop` arg of
various bank and register methods is no longer present. This has
been replaced with an argument `void *aux`, which is
normally NULL.  If some register in a bank needs a memop, then the
`io_memory_access` method can be updated to pass down the
memop in the `aux` argument (just call `default`
with `memop` in the last arg). An explicit call to a bank
method, e.g. a redirection of an access to a different bank,
should normally be rewritten as a call to `read` or
`write`, usually with NULL in the `aux`
argument.

Bank methods are converted as follows: `access` →
`io_memory_access`; `read_access`,
`read_access_memop` → `read`;
`write_access`, `write_access_memop` →
`write`

Register methods are converted like so: `read_access`
→ `read_register`, `write_access` →
`write_register`

Field methods are converted thusly: `read_access`
→ `read_field`, `write_access` →
`write_field`

In `register` and `field` objects, the
`set` and
`write_register`/`write_field` methods will get
an explicit type `uint64`.

The read and write methods on `bank`, `register`,
and `field` objects all take a new `uint64` argument
denoting enabled bytes or bits, depending on the context, which
may mask an access.

In `connect` objects, `validate_port` is converted
to `validate`; named ports are deprecated in Simics 6, but
the port name is available in the `port` session variable.

In `attribute` objects, the `set` method will get
an explicit argument type `attr_value_t`, and a
`throws` annotation.
</dd>
  <dt>PCONSTANT</dt>
  <dd>

`constant` declarations are removed in 1.4 and should be
replaced with `param` declarations. Both are accessible
from the top-level scope of a device.
</dd>
  <dt>PDOLLAR_QUALIFY</dt>
  <dd>

In DML 1.4, there is no separate scope for `$`, so local
variables can shadow object references. This conversion rule
attempts to detect this, and add `this.` or
<tt>dev.<i>path</i>.</tt> where needed.
</dd>
  <dt>PEVENT</dt>
  <dd>

Event objects no longer have the `timebase` parameter;
instead you must choose a standard template to instantiate. The
conversion script will pick `custom_time_event` or
`custom_cycle_event`.
</dd>
  <dt>PFIELDRANGE</dt>
  <dd>

In a field declaration, the field range declaration must be
preceded by `@`. In DML 1.4, the syntax `field f[4]`
declares a field array of size 4, while in DML 1.2 it denotes a field
occupying bit 4 in its parent register.
</dd>
  <dt>PHARD_RESET_VALUE</dt>
  <dd>

The `hard_reset_value` parameter is no longer
recognized. The parameter is automatically renamed to
`init_val`, which has roughly the same effect.
</dd>
  <dt>PHASH</dt>
  <dd>

`if` statements on top level must be prefixed with a `#`
character. The same applies to `if` statement inside a method body
if the condition is constant and the dead branch contains errors.

Similarly, the conditional operator (`? :`) is updated to #? #:
when needed, `select` is updated to `#select`, and
`foreach` is updated to `#foreach`.
</dd>
  <dt>PHASHELSE</dt>
  <dd>

If an `if` is updated to `#if`, and there is a
corresponding `else` clause, then it must be updated to
`#else`. The same applies to the `else` clause in
`select` statements.
</dd>
  <dt>PIFAND</dt>
  <dd>

If statements on the form `if (defined(X) && X.y) { ... }`
are converted to a nested `#if` statement
</dd>
  <dt>PIMPORT_DML12COMPAT</dt>
  <dd>

The `PTRAMPOLINE` porting rule sometimes requires
that `dml12-compatibility.dml` is imported.
</dd>
  <dt>PINARGTYPE</dt>
  <dd>

When overriding a method in DML 1.4, the overriding and default
implementation must declare the same arguments as `inline`.
If the override has untyped arguments that are typed in the default
method, then the conversion script will add a type to the override's
argument.

Note: The inserted type declaration uses C syntax, which in most
cases matches DML syntax; however, there are exceptions where the
inserted declaration will be broken and needs to be fixed manually.
</dd>
  <dt>PINLINEDECL</dt>
  <dd>

Methods with untyped parameters must be explicitly marked 'inline'
in DML 1.4, as in `inline method m(inline x) -> (int y)`
</dd>
  <dt>PINPARAMLIST</dt>
  <dd>

If a method has no input arguments, the empty input parameter
list `()` is now required in method declarations
and `call`/`inline` statements.
</dd>
  <dt>PINVOKE</dt>
  <dd>

Method invocation syntax changed. Replace

```
call m(x) -> (a, b);
inline n() -> (c);
call o();
```
with:
```
(a, b) = m(x);
c = n();
o();
```
</dd>
  <dt>PLOGKIND</dt>
  <dd>

In log statements, the old syntax where log type is denoted by a string
has been removed. Use the new identifier-based syntax instead. E.g.,
instead of:
```
log "info": "foo";
log "spec_violation": "foo";
```
you must now write:
```
log info: "foo";
log spec_viol: "foo";
```
</dd>
  <dt>PMISS_PATTERN</dt>
  <dd>

The `miss_pattern` parameter is no longer recognized by
banks, unless the `miss_pattern_bank` template, from utility.dml, is
instantiated.  An instantiation is automatically added.
</dd>
  <dt>PNODOLLAR</dt>
  <dd>

The `$` character is no longer needed when referencing objects.
</dd>
  <dt>PNOTHROW</dt>
  <dd>

In DML 1.4, it is assumed by default that a method may not throw an
exception. Any `nothrow` annotations must be removed.
</dd>
  <dt>PNO_WUNUSED</dt>
  <dd>

Used in conjunction with PWUNUSED to signal that a piece of
conditional code was indeed used. If using multiple runs of DMLC
as input to the porting script, and a piece of code was used in
some runs and unused in others, then no warning is shown.
</dd>
  <dt>POVERRIDE</dt>
  <dd>

If a method has exactly one default and one non-default
declaration, and the non-default declaration resides in a
template, then DML 1.4 requires that this template inherits from
the template containing the default declaration. Conversion is done
automatically for the most common case.
</dd>
  <dt>POVERRIDE_IMPORT</dt>
  <dd>

Similar to POVERRIDE, but if a default method does _not_
reside in a template, then the file that instantiates the non-default
declaration must import the file containing the default declaration.
</dd>
  <dt>PPARAMETER</dt>
  <dd>

The `parameter` keyword has been renamed to `param`.
</dd>
  <dt>PRENAME_TEMPLATE</dt>
  <dd>

Some templates in `utility.dml` have been renamed; in
particular, `unimplemented` has been renamed to
`unimpl`.
</dd>
  <dt>PRETURNARGS</dt>
  <dd>

In methods with return values, return statements now take arguments:
```
method m() -> (int, int) {
return (1, 4);
}
method n() -> (int) {
return 3;
}
```
</dd>
  <dt>PRETVAL</dt>
  <dd>

Method output parameters are not named in DML 1.4:
```
method m() -> (int, int) {
...
}
```

See also PRETURNARGS.
</dd>
  <dt>PSESSION</dt>
  <dd>

The `data` and `static` keywords have both been replaced
with `session`:
```
session uint32 x;
```
</dd>
  <dt>PSHA1</dt>
  <dd>

The `port-dml` script requires that the DML file has not been
changed since the tag file was generated. This is verified by a
SHA1 checksum.
</dd>
  <dt>PSOFT_RESET_VALUE</dt>
  <dd>

The `soft_reset_value` parameter is renamed to
`soft_reset_val`, and requires the template
`soft_reset_val` to be instantiated.
</dd>
  <dt>PSTRINGIFY</dt>
  <dd>

In DML 1.4, `#` is changed to the
`stringify` operator
</dd>
  <dt>PSTRUCTDECL</dt>
  <dd>

Struct type definitions can no longer be declared using the
labeled struct syntax. The equivalent typedef declaration should
be used instead. For example, the following is now disallowed:

<pre>
struct <var>xyz</var> { ... }
</pre>

and should be replaced with the following:

<pre>
typedef struct { ... } <var>xyz</var>;
</pre>
</dd>
  <dt>PTHROWS</dt>
  <dd>

In DML 1.4, methods that can throw an exception must explicitly
declare that with a 'throws' annotation. Such annotation is
automatically added for methods that override a throwing method
that was declared in a DML 1.4 file.
</dd>
  <dt>PTRAMPOLINE</dt>
  <dd>

The methods `miss_read_access` and
`miss_write_access` in `bank` objects have been
renamed to `unmapped_read` and `unmapped_write`
in 1.4. The converter creates methods with the new names, which
call the existing unmodified methods.
</dd>
  <dt>PTYPEDOUTPARAM</dt>
  <dd>

Method output parameters must have explicit types in DML 1.4. The
automatic conversion script will convert untyped output parameters
to `uint64`.
</dd>
  <dt>PVAL</dt>
  <dd>

The value of a `register`, `field` or `attribute`
object, and the interface struct of a `interface` object, is now
accessed through the `.val` member.
</dd>
  <dt>PVERSION</dt>
  <dd>

DML 1.4 files should start with `dml 1.4;` instead
of `dml 1.2;`
</dd>
  <dt>PWUNUSED</dt>
  <dd>

This message is used to signal to the porting script that a piece
of conditional code was not fully covered by the compile. Some
portings are never applied on dead code. The porting script
can signal a warning for this.
</dd>
</dl>
