<!--
  © 2021-2022 Intel Corporation
  SPDX-License-Identifier: MPL-2.0
-->
<dl>
<dt><i>dml</i> &rarr;</dt>
<dd>
 <b>device</b> <i> objident </i> "<b>;</b>" <i> maybe_bitorder </i> <i> device_statements </i> <br/><b>|</b> <i> maybe_bitorder </i> <i> device_statements </i> </dd>
<dt><i>maybe_bitorder</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <b>bitorder</b> <i> ident </i> "<b>;</b>" </dd>
<dt><i>device_statements</i> &rarr;</dt>
<dd>
 <i> device_statements </i> <i> device_statement </i> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>device_statement</i> &rarr;</dt>
<dd>
 <i> toplevel </i> <br/><b>|</b> <i> object </i> <br/><b>|</b> <i> parameter </i> <br/><b>|</b> <i> method </i> <br/><b>|</b> <i> bad_shared_method </i> <br/><b>|</b> <i> istemplate </i> "<b>;</b>" <br/><b>|</b> <i> toplevel_if </i> <br/><b>|</b> <i> error_stmt </i> <br/><b>|</b> <i> in_each </i> </dd>
<dt><i>toplevel_if</i> &rarr;</dt>
<dd>
 <i> hashif </i> "<b>(</b>" <i> expression </i> "<b>)</b>" "<b>{</b>" <i> device_statements </i> "<b>}</b>" <i> toplevel_else </i> </dd>
<dt><i>toplevel_else</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> hashelse </i> "<b>{</b>" <i> device_statements </i> "<b>}</b>" <br/><b>|</b> <i> hashelse </i> <i> toplevel_if </i> </dd>
<dt><i>array_list</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> array_list </i> "<b>[</b>" <i> arraydef </i> "<b>]</b>" </dd>
<dt><i>object</i> &rarr;</dt>
<dd>
 <b>register</b> <i> objident </i> <i> array_list </i> <i> sizespec </i> <i> offsetspec </i> <i> maybe_istemplate </i> <i> object_spec </i> </dd>
<dt><i>bitrangespec</i> &rarr;</dt>
<dd>
 "<b>@</b>" <i> bitrange </i> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>object</i> &rarr;</dt>
<dd>
 <b>field</b> <i> objident </i> <i> array_list </i> <i> bitrangespec </i> <i> maybe_istemplate </i> <i> object_spec </i> </dd>
<dt><i>bitrange</i> &rarr;</dt>
<dd>
 "<b>[</b>" <i> expression </i> "<b>]</b>" <br/><b>|</b> "<b>[</b>" <i> expression </i> "<b>:</b>" <i> expression </i> "<b>]</b>" </dd>
<dt><i>data</i> &rarr;</dt>
<dd>
 <b>session</b> </dd>
<dt><i>object</i> &rarr;</dt>
<dd>
 <i> session_decl </i> </dd>
<dt><i>session_decl</i> &rarr;</dt>
<dd>
 <i> data </i> <i> named_cdecl </i> "<b>;</b>" <br/><b>|</b> <i> data </i> <i> named_cdecl </i> "<b>=</b>" <i> initializer </i> "<b>;</b>" </dd>
<dt><i>object</i> &rarr;</dt>
<dd>
 <i> saved_decl </i> </dd>
<dt><i>saved_decl</i> &rarr;</dt>
<dd>
 <b>saved</b> <i> named_cdecl </i> "<b>;</b>" <br/><b>|</b> <b>saved</b> <i> named_cdecl </i> "<b>=</b>" <i> initializer </i> "<b>;</b>" </dd>
<dt><i>object</i> &rarr;</dt>
<dd>
 <b>connect</b> <i> objident </i> <i> array_list </i> <i> maybe_istemplate </i> <i> object_spec </i> <br/><b>|</b> <b>interface</b> <i> objident </i> <i> array_list </i> <i> maybe_istemplate </i> <i> object_spec </i> <br/><b>|</b> <b>attribute</b> <i> objident </i> <i> array_list </i> <i> maybe_istemplate </i> <i> object_spec </i> <br/><b>|</b> <b>bank</b> <i> objident </i> <i> array_list </i> <i> maybe_istemplate </i> <i> object_spec </i> <br/><b>|</b> <b>event</b> <i> objident </i> <i> array_list </i> <i> maybe_istemplate </i> <i> object_spec </i> <br/><b>|</b> <b>group</b> <i> objident </i> <i> array_list </i> <i> maybe_istemplate </i> <i> object_spec </i> <br/><b>|</b> <b>port</b> <i> objident </i> <i> array_list </i> <i> maybe_istemplate </i> <i> object_spec </i> <br/><b>|</b> <b>implement</b> <i> objident </i> <i> array_list </i> <i> maybe_istemplate </i> <i> object_spec </i> <br/><b>|</b> <b>subdevice</b> <i> objident </i> <i> array_list </i> <i> maybe_istemplate </i> <i> object_spec </i> </dd>
<dt><i>maybe_default</i> &rarr;</dt>
<dd>
 <b>default</b> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>method</i> &rarr;</dt>
<dd>
 <b>method</b> <i> objident </i> <i> method_params_typed </i> <i> maybe_default </i> <i> compound_statement </i> <br/><b>|</b> <b>inline</b> <b>method</b> <i> objident </i> <i> method_params_maybe_untyped </i> <i> maybe_default </i> <i> compound_statement </i> </dd>
<dt><i>arraydef</i> &rarr;</dt>
<dd>
 <i> ident </i> "<b>&lt;</b>" <i> expression </i> <br/><b>|</b> <i> ident </i> "<b>&lt;</b>" <i>"..."</i> </dd>
<dt><i>template_stmts</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> template_stmts </i> <i> template_stmt </i> </dd>
<dt><i>template_stmt</i> &rarr;</dt>
<dd>
 <i> object_statement_or_typedparam </i> <br/><b>|</b> <b>shared</b> <b>method</b> <i> shared_method </i> </dd>
<dt><i>shared_method</i> &rarr;</dt>
<dd>
 <i> ident </i> <i> method_params_typed </i> "<b>;</b>" <br/><b>|</b> <i> ident </i> <i> method_params_typed </i> <b>default</b> <i> compound_statement </i> <br/><b>|</b> <i> ident </i> <i> method_params_typed </i> <i> compound_statement </i> </dd>
<dt><i>param_</i> &rarr;</dt>
<dd>
 <b>param</b> </dd>
<dt><i>toplevel</i> &rarr;</dt>
<dd>
 <b>template</b> <i> objident </i> <i> maybe_istemplate </i> "<b>{</b>" <i> template_stmts </i> "<b>}</b>" <br/><b>|</b> <b>header</b> "<b>%{ ... %}</b>" <br/><b>|</b> <b>footer</b> "<b>%{ ... %}</b>" <br/><b>|</b> <b>_header</b> "<b>%{ ... %}</b>" <br/><b>|</b> <b>loggroup</b> <i> ident </i> "<b>;</b>" <br/><b>|</b> <b>constant</b> <i> ident </i> "<b>=</b>" <i> expression </i> "<b>;</b>" <br/><b>|</b> <b>extern</b> <i> cdecl </i> "<b>;</b>" <br/><b>|</b> <b>typedef</b> <i> named_cdecl </i> "<b>;</b>" <br/><b>|</b> <b>extern</b> <b>typedef</b> <i> named_cdecl </i> "<b>;</b>" <br/><b>|</b> <b>import</b> <i> utf8_sconst </i> "<b>;</b>" </dd>
<dt><i>object_desc</i> &rarr;</dt>
<dd>
 <i> composed_string_literal </i> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>object_spec</i> &rarr;</dt>
<dd>
 <i> object_desc </i> "<b>;</b>" <br/><b>|</b> <i> object_desc </i> "<b>{</b>" <i> object_statements </i> "<b>}</b>" </dd>
<dt><i>object_statements</i> &rarr;</dt>
<dd>
 <i> object_statements </i> <i> object_statement </i> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>object_statement</i> &rarr;</dt>
<dd>
 <i> object_statement_or_typedparam </i> <br/><b>|</b> <i> bad_shared_method </i> </dd>
<dt><i>bad_shared_method</i> &rarr;</dt>
<dd>
 <b>shared</b> <b>method</b> <i> shared_method </i> </dd>
<dt><i>toplevel</i> &rarr;</dt>
<dd>
 <b>export</b> <i> expression </i> <b>as</b> <i> expression </i> "<b>;</b>" </dd>
<dt><i>object_statement_or_typedparam</i> &rarr;</dt>
<dd>
 <i> object </i> <br/><b>|</b> <i> parameter </i> <br/><b>|</b> <i> method </i> <br/><b>|</b> <i> istemplate </i> "<b>;</b>" <br/><b>|</b> <i> object_if </i> <br/><b>|</b> <i> error_stmt </i> <br/><b>|</b> <i> in_each </i> </dd>
<dt><i>in_each</i> &rarr;</dt>
<dd>
 <b>in</b> <b>each</b> <i> istemplate_list </i> "<b>{</b>" <i> object_statements </i> "<b>}</b>" </dd>
<dt><i>hashif</i> &rarr;</dt>
<dd>
 "<b>#if</b>" <br/><b>|</b> <b>if</b> </dd>
<dt><i>hashelse</i> &rarr;</dt>
<dd>
 "<b>#else</b>" <br/><b>|</b> <b>else</b> </dd>
<dt><i>object_if</i> &rarr;</dt>
<dd>
 <i> hashif </i> "<b>(</b>" <i> expression </i> "<b>)</b>" "<b>{</b>" <i> object_statements </i> "<b>}</b>" <i> object_else </i> </dd>
<dt><i>object_else</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> hashelse </i> "<b>{</b>" <i> object_statements </i> "<b>}</b>" <br/><b>|</b> <i> hashelse </i> <i> object_if </i> </dd>
<dt><i>parameter</i> &rarr;</dt>
<dd>
 <i> param_ </i> <i> objident </i> <i> paramspec </i> <br/><b>|</b> <i> param_ </i> <i> objident </i> "<b>:</b>" <i> ctypedecl </i> "<b>;</b>" </dd>
<dt><i>paramspec</i> &rarr;</dt>
<dd>
 "<b>;</b>" <br/><b>|</b> "<b>=</b>" <i> expression </i> "<b>;</b>" <br/><b>|</b> <b>default</b> <i> expression </i> "<b>;</b>" <br/><b>|</b> <b>auto</b> "<b>;</b>" </dd>
<dt><i>method_outparams</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> "<b>-&gt;</b>" "<b>(</b>" <i> cdecl_list </i> "<b>)</b>" </dd>
<dt><i>method_params_maybe_untyped</i> &rarr;</dt>
<dd>
 "<b>(</b>" <i> cdecl_or_ident_list </i> "<b>)</b>" <i> method_outparams </i> <i> throws </i> </dd>
<dt><i>method_params_typed</i> &rarr;</dt>
<dd>
 "<b>(</b>" <i> cdecl_list </i> "<b>)</b>" <i> method_outparams </i> <i> throws </i> </dd>
<dt><i>throws</i> &rarr;</dt>
<dd>
 <b>throws</b> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>maybe_istemplate</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> istemplate </i> </dd>
<dt><i>istemplate</i> &rarr;</dt>
<dd>
 <b>is</b> <i> istemplate_list </i> </dd>
<dt><i>istemplate_list</i> &rarr;</dt>
<dd>
 <i> objident </i> <br/><b>|</b> "<b>(</b>" <i> objident_list </i> "<b>)</b>" </dd>
<dt><i>sizespec</i> &rarr;</dt>
<dd>
 <b>size</b> <i> expression </i> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>offsetspec</i> &rarr;</dt>
<dd>
 "<b>@</b>" <i> expression </i> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>cdecl_or_ident</i> &rarr;</dt>
<dd>
 <i> named_cdecl </i> <br/><b>|</b> <b>inline</b> <i> ident </i> </dd>
<dt><i>named_cdecl</i> &rarr;</dt>
<dd>
 <i> cdecl </i> </dd>
<dt><i>cdecl</i> &rarr;</dt>
<dd>
 <i> basetype </i> <i> cdecl2 </i> <br/><b>|</b> <b>const</b> <i> basetype </i> <i> cdecl2 </i> </dd>
<dt><i>basetype</i> &rarr;</dt>
<dd>
 <i> typeident </i> <br/><b>|</b> <i> struct </i> <br/><b>|</b> <i> layout </i> <br/><b>|</b> <i> bitfields </i> <br/><b>|</b> <i> typeof </i> <br/><b>|</b> <b>sequence</b> "<b>(</b>" <i> typeident </i> "<b>)</b>" </dd>
<dt><i>cdecl2</i> &rarr;</dt>
<dd>
 <i> cdecl3 </i> <br/><b>|</b> <b>const</b> <i> cdecl2 </i> <br/><b>|</b> "<b>*</b>" <i> cdecl2 </i> <br/><b>|</b> <b>vect</b> <i> cdecl2 </i> </dd>
<dt><i>cdecl3</i> &rarr;</dt>
<dd>
 <i> ident </i> <br/><b>|</b> &lt;empty&gt; <br/><b>|</b> <i> cdecl3 </i> "<b>[</b>" <i> expression </i> "<b>]</b>" <br/><b>|</b> <i> cdecl3 </i> "<b>(</b>" <i> cdecl_list_opt_ellipsis </i> "<b>)</b>" <br/><b>|</b> "<b>(</b>" <i> cdecl2 </i> "<b>)</b>" </dd>
<dt><i>cdecl_list</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> cdecl_list_nonempty </i> </dd>
<dt><i>cdecl_list_nonempty</i> &rarr;</dt>
<dd>
 <i> cdecl </i> <br/><b>|</b> <i> cdecl_list_nonempty </i> "<b>,</b>" <i> cdecl </i> </dd>
<dt><i>cdecl_list_opt_ellipsis</i> &rarr;</dt>
<dd>
 <i> cdecl_list </i> <br/><b>|</b> <i> cdecl_list_ellipsis </i> </dd>
<dt><i>cdecl_list_ellipsis</i> &rarr;</dt>
<dd>
 <i>"..."</i> <br/><b>|</b> <i> cdecl_list_nonempty </i> "<b>,</b>" <i>"..."</i> </dd>
<dt><i>cdecl_or_ident_list</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> cdecl_or_ident_list2 </i> </dd>
<dt><i>cdecl_or_ident_list2</i> &rarr;</dt>
<dd>
 <i> cdecl_or_ident </i> <br/><b>|</b> <i> cdecl_or_ident_list2 </i> "<b>,</b>" <i> cdecl_or_ident </i> </dd>
<dt><i>typeof</i> &rarr;</dt>
<dd>
 <b>typeof</b> <i> expression </i> </dd>
<dt><i>struct</i> &rarr;</dt>
<dd>
 <b>struct</b> "<b>{</b>" <i> struct_decls </i> "<b>}</b>" </dd>
<dt><i>struct_decls</i> &rarr;</dt>
<dd>
 <i> struct_decls </i> <i> named_cdecl </i> "<b>;</b>" <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>layout_decl</i> &rarr;</dt>
<dd>
 <b>layout</b> <i> utf8_sconst </i> "<b>{</b>" <i> layout_decls </i> "<b>}</b>" </dd>
<dt><i>layout</i> &rarr;</dt>
<dd>
 <i> layout_decl </i> </dd>
<dt><i>layout_decls</i> &rarr;</dt>
<dd>
 <i> layout_decls </i> <i> named_cdecl </i> "<b>;</b>" <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>bitfields</i> &rarr;</dt>
<dd>
 <b>bitfields</b> <i>integer-literal</i> "<b>{</b>" <i> bitfields_decls </i> "<b>}</b>" </dd>
<dt><i>bitfields_decls</i> &rarr;</dt>
<dd>
 <i> bitfields_decls </i> <i> named_cdecl </i> "<b>@</b>" "<b>[</b>" <i> bitfield_range </i> "<b>]</b>" "<b>;</b>" </dd>
<dt><i>bitfield_range</i> &rarr;</dt>
<dd>
 <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>:</b>" <i> expression </i> </dd>
<dt><i>bitfields_decls</i> &rarr;</dt>
<dd>
 &lt;empty&gt; </dd>
<dt><i>ctypedecl</i> &rarr;</dt>
<dd>
 <i> const_opt </i> <i> basetype </i> <i> ctypedecl_ptr </i> </dd>
<dt><i>ctypedecl_ptr</i> &rarr;</dt>
<dd>
 <i> stars </i> <i> ctypedecl_array </i> </dd>
<dt><i>stars</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> "<b>*</b>" <b>const</b> <i> stars </i> <br/><b>|</b> "<b>*</b>" <i> stars </i> </dd>
<dt><i>ctypedecl_array</i> &rarr;</dt>
<dd>
 <i> ctypedecl_simple </i> </dd>
<dt><i>ctypedecl_simple</i> &rarr;</dt>
<dd>
 "<b>(</b>" <i> ctypedecl_ptr </i> "<b>)</b>" <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>const_opt</i> &rarr;</dt>
<dd>
 <b>const</b> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>typeident</i> &rarr;</dt>
<dd>
 <i> ident </i> <br/><b>|</b> <b>char</b> <br/><b>|</b> <b>double</b> <br/><b>|</b> <b>float</b> <br/><b>|</b> <b>int</b> <br/><b>|</b> <b>long</b> <br/><b>|</b> <b>short</b> <br/><b>|</b> <b>signed</b> <br/><b>|</b> <b>unsigned</b> <br/><b>|</b> <b>void</b> <br/><b>|</b> <b>register</b> </dd>
<dt><i>assignop</i> &rarr;</dt>
<dd>
 <i> expression </i> "<b>+=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>-=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>*=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>/=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>%=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>|=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&amp;=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>^=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&lt;&lt;=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&gt;&gt;=</b>" <i> expression </i> </dd>
<dt><i>expression</i> &rarr;</dt>
<dd>
 <i> expression </i> "<b>?</b>" <i> expression </i> "<b>:</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> <b>#?</b> <i> expression </i> <b>#:</b> <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>+</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>-</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>*</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>/</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>%</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&lt;&lt;</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&gt;&gt;</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>==</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>!=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&lt;</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&gt;</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&lt;=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&gt;=</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>||</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&amp;&amp;</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>|</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>^</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>&amp;</b>" <i> expression </i> <br/><b>|</b> <b>cast</b> "<b>(</b>" <i> expression </i> "<b>,</b>" <i> ctypedecl </i> "<b>)</b>" <br/><b>|</b> <b>sizeof</b> <i> expression </i> <br/><b>|</b> "<b>-</b>" <i> expression </i> <br/><b>|</b> "<b>+</b>" <i> expression </i> <br/><b>|</b> "<b>!</b>" <i> expression </i> <br/><b>|</b> "<b>~</b>" <i> expression </i> <br/><b>|</b> "<b>&amp;</b>" <i> expression </i> <br/><b>|</b> "<b>*</b>" <i> expression </i> <br/><b>|</b> <b>defined</b> <i> expression </i> <br/><b>|</b> <b>stringify</b> "<b>(</b>" <i> expression </i> "<b>)</b>" <br/><b>|</b> "<b>++</b>" <i> expression </i> <br/><b>|</b> "<b>--</b>" <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>++</b>" <br/><b>|</b> <i> expression </i> "<b>--</b>" <br/><b>|</b> <i> expression </i> "<b>(</b>" <i> expression_list </i> "<b>)</b>" <br/><b>|</b> <i>integer-literal</i> <br/><b>|</b> <i>hex-literal</i> <br/><b>|</b> <i>binary-literal</i> <br/><b>|</b> <i>char-literal</i> <br/><b>|</b> <i>float-literal</i> <br/><b>|</b> <i>string-literal</i> </dd>
<dt><i>utf8_sconst</i> &rarr;</dt>
<dd>
 <i>string-literal</i> </dd>
<dt><i>expression</i> &rarr;</dt>
<dd>
 <b>undefined</b> <br/><b>|</b> <i> objident </i> <br/><b>|</b> <b>default</b> <br/><b>|</b> <b>this</b> <br/><b>|</b> <i> expression </i> "<b>.</b>" <i> objident </i> <br/><b>|</b> <i> expression </i> "<b>-&gt;</b>" <i> objident </i> <br/><b>|</b> <b>sizeoftype</b> <i> typeoparg </i> </dd>
<dt><i>typeoparg</i> &rarr;</dt>
<dd>
 <i> ctypedecl </i> <br/><b>|</b> "<b>(</b>" <i> ctypedecl </i> "<b>)</b>" </dd>
<dt><i>expression</i> &rarr;</dt>
<dd>
 <b>new</b> <i> ctypedecl </i> <br/><b>|</b> <b>new</b> <i> ctypedecl </i> "<b>[</b>" <i> expression </i> "<b>]</b>" <br/><b>|</b> "<b>(</b>" <i> expression </i> "<b>)</b>" <br/><b>|</b> "<b>[</b>" <i> expression_list </i> "<b>]</b>" <br/><b>|</b> <i> expression </i> "<b>[</b>" <i> expression </i> "<b>]</b>" <br/><b>|</b> <i> expression </i> "<b>[</b>" <i> expression </i> "<b>,</b>" <i>identifier</i> "<b>]</b>" <br/><b>|</b> <i> expression </i> "<b>[</b>" <i> expression </i> "<b>:</b>" <i> expression </i> <i> endianflag </i> "<b>]</b>" <br/><b>|</b> <b>each</b> <i> objident </i> <b>in</b> "<b>(</b>" <i> expression </i> "<b>)</b>" </dd>
<dt><i>endianflag</i> &rarr;</dt>
<dd>
 "<b>,</b>" <i>identifier</i> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>expression_opt</i> &rarr;</dt>
<dd>
 <i> expression </i> <br/><b>|</b> &lt;empty&gt; </dd>
<dt><i>expression_list</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>,</b>" <i> expression_list </i> </dd>
<dt><i>expression_list_ntc_nonempty</i> &rarr;</dt>
<dd>
 <i> expression </i> <br/><b>|</b> <i> expression </i> "<b>,</b>" <i> expression_list_ntc_nonempty </i> </dd>
<dt><i>composed_string_literal</i> &rarr;</dt>
<dd>
 <i> utf8_sconst </i> <br/><b>|</b> <i> composed_string_literal </i> "<b>+</b>" <i> utf8_sconst </i> </dd>
<dt><i>bracketed_string_literal</i> &rarr;</dt>
<dd>
 <i> composed_string_literal </i> <br/><b>|</b> "<b>(</b>" <i> composed_string_literal </i> "<b>)</b>" </dd>
<dt><i>initializer</i> &rarr;</dt>
<dd>
 <i> expression </i> <br/><b>|</b> "<b>{</b>" <i> initializer_list </i> "<b>}</b>" <br/><b>|</b> "<b>{</b>" <i> initializer_list </i> "<b>,</b>" "<b>}</b>" </dd>
<dt><i>initializer_list</i> &rarr;</dt>
<dd>
 <i> initializer </i> <br/><b>|</b> <i> initializer_list </i> "<b>,</b>" <i> initializer </i> </dd>
<dt><i>initializer</i> &rarr;</dt>
<dd>
 "<b>{</b>" <i> designated_struct_initializer_list </i> "<b>}</b>" <br/><b>|</b> "<b>{</b>" <i> designated_struct_initializer_list </i> "<b>,</b>" "<b>}</b>" </dd>
<dt><i>designated_struct_initializer</i> &rarr;</dt>
<dd>
 "<b>.</b>" <i> ident </i> "<b>=</b>" <i> initializer </i> </dd>
<dt><i>designated_struct_initializer_list</i> &rarr;</dt>
<dd>
 <i> designated_struct_initializer </i> <br/><b>|</b> <i> designated_struct_initializer_list </i> "<b>,</b>" <i> designated_struct_initializer </i> </dd>
<dt><i>statement</i> &rarr;</dt>
<dd>
 <i> statement_except_hashif </i> </dd>
<dt><i>statement_except_hashif</i> &rarr;</dt>
<dd>
 <i> compound_statement </i> <br/><b>|</b> <i> local </i> "<b>;</b>" <br/><b>|</b> <i> saved_decl </i> <br/><b>|</b> <i> assign_stmt </i> "<b>;</b>" <br/><b>|</b> <i> assignop </i> "<b>;</b>" </dd>
<dt><i>assign_stmt</i> &rarr;</dt>
<dd>
 <i> assign_chain </i> </dd>
<dt><i>assign_chain</i> &rarr;</dt>
<dd>
 <i> assign_target </i> "<b>=</b>" <i> assign_chain </i> <br/><b>|</b> <i> assign_target </i> "<b>=</b>" <i> initializer </i> </dd>
<dt><i>assign_target</i> &rarr;</dt>
<dd>
 <i> expression </i> <br/><b>|</b> "<b>(</b>" <i> expression </i> "<b>,</b>" <i> expression_list_ntc_nonempty </i> "<b>)</b>" </dd>
<dt><i>statement_except_hashif</i> &rarr;</dt>
<dd>
 "<b>;</b>" <br/><b>|</b> <i> expression </i> "<b>;</b>" <br/><b>|</b> <b>if</b> "<b>(</b>" <i> expression </i> "<b>)</b>" <i> statement </i> <br/><b>|</b> <b>if</b> "<b>(</b>" <i> expression </i> "<b>)</b>" <i> statement </i> <b>else</b> <i> statement </i> </dd>
<dt><i>statement</i> &rarr;</dt>
<dd>
 "<b>#if</b>" "<b>(</b>" <i> expression </i> "<b>)</b>" <i> statement </i> <br/><b>|</b> "<b>#if</b>" "<b>(</b>" <i> expression </i> "<b>)</b>" <i> statement </i> "<b>#else</b>" <i> statement </i> </dd>
<dt><i>statement_except_hashif</i> &rarr;</dt>
<dd>
 <b>while</b> "<b>(</b>" <i> expression </i> "<b>)</b>" <i> statement </i> <br/><b>|</b> <b>do</b> <i> statement </i> <b>while</b> "<b>(</b>" <i> expression </i> "<b>)</b>" "<b>;</b>" </dd>
<dt><i>for_post</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> for_post_nonempty </i> </dd>
<dt><i>for_post_nonempty</i> &rarr;</dt>
<dd>
 <i> for_post_one </i> <br/><b>|</b> <i> for_post_nonempty </i> "<b>,</b>" <i> for_post_one </i> </dd>
<dt><i>for_post_one</i> &rarr;</dt>
<dd>
 <i> assign_stmt </i> <br/><b>|</b> <i> assignop </i> <br/><b>|</b> <i> expression </i> </dd>
<dt><i>for_pre</i> &rarr;</dt>
<dd>
 <i> local </i> <br/><b>|</b> <i> for_post </i> </dd>
<dt><i>statement_except_hashif</i> &rarr;</dt>
<dd>
 <b>for</b> "<b>(</b>" <i> for_pre </i> "<b>;</b>" <i> expression_opt </i> "<b>;</b>" <i> for_post </i> "<b>)</b>" <i> statement </i> <br/><b>|</b> <b>switch</b> "<b>(</b>" <i> expression </i> "<b>)</b>" "<b>{</b>" <i> stmt_or_case_list </i> "<b>}</b>" </dd>
<dt><i>stmt_or_case</i> &rarr;</dt>
<dd>
 <i> statement_except_hashif </i> <br/><b>|</b> <i> cond_case_statement </i> <br/><b>|</b> <i> case_statement </i> </dd>
<dt><i>cond_case_statement</i> &rarr;</dt>
<dd>
 "<b>#if</b>" "<b>(</b>" <i> expression </i> "<b>)</b>" "<b>{</b>" <i> stmt_or_case_list </i> "<b>}</b>" <br/><b>|</b> "<b>#if</b>" "<b>(</b>" <i> expression </i> "<b>)</b>" "<b>{</b>" <i> stmt_or_case_list </i> "<b>}</b>" "<b>#else</b>" "<b>{</b>" <i> stmt_or_case_list </i> "<b>}</b>" </dd>
<dt><i>stmt_or_case_list</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> stmt_or_case_list </i> <i> stmt_or_case </i> </dd>
<dt><i>statement_except_hashif</i> &rarr;</dt>
<dd>
 <b>delete</b> <i> expression </i> "<b>;</b>" <br/><b>|</b> <b>try</b> <i> statement </i> <b>catch</b> <i> statement </i> <br/><b>|</b> <b>after</b> <i> expression </i> <i>identifier</i> "<b>:</b>" <i> expression </i> "<b>;</b>" <br/><b>|</b> <b>assert</b> <i> expression </i> "<b>;</b>" </dd>
<dt><i>log_kind</i> &rarr;</dt>
<dd>
 <i>identifier</i> <br/><b>|</b> <b>error</b> </dd>
<dt><i>log_level</i> &rarr;</dt>
<dd>
 <i> expression </i> <b>then</b> <i> expression </i> <br/><b>|</b> <i> expression </i> </dd>
<dt><i>statement_except_hashif</i> &rarr;</dt>
<dd>
 <b>log</b> <i> log_kind </i> "<b>,</b>" <i> log_level </i> "<b>,</b>" <i> expression </i> "<b>:</b>" <i> bracketed_string_literal </i> <i> log_args </i> "<b>;</b>" <br/><b>|</b> <b>log</b> <i> log_kind </i> "<b>,</b>" <i> log_level </i> "<b>:</b>" <i> bracketed_string_literal </i> <i> log_args </i> "<b>;</b>" <br/><b>|</b> <b>log</b> <i> log_kind </i> "<b>:</b>" <i> bracketed_string_literal </i> <i> log_args </i> "<b>;</b>" </dd>
<dt><i>hashselect</i> &rarr;</dt>
<dd>
 "<b>#select</b>" </dd>
<dt><i>statement_except_hashif</i> &rarr;</dt>
<dd>
 <i> hashselect </i> <i> ident </i> <b>in</b> "<b>(</b>" <i> expression </i> "<b>)</b>" <b>where</b> "<b>(</b>" <i> expression </i> "<b>)</b>" <i> statement </i> <i> hashelse </i> <i> statement </i> <br/><b>|</b> <b>foreach</b> <i> ident </i> <b>in</b> "<b>(</b>" <i> expression </i> "<b>)</b>" <i> statement </i> <br/><b>|</b> "<b>#foreach</b>" <i> ident </i> <b>in</b> "<b>(</b>" <i> expression </i> "<b>)</b>" <i> statement </i> </dd>
<dt><i>case_statement</i> &rarr;</dt>
<dd>
 <b>case</b> <i> expression </i> "<b>:</b>" <br/><b>|</b> <b>default</b> "<b>:</b>" </dd>
<dt><i>statement_except_hashif</i> &rarr;</dt>
<dd>
 <b>goto</b> <i> ident </i> "<b>;</b>" <br/><b>|</b> <b>break</b> "<b>;</b>" <br/><b>|</b> <b>continue</b> "<b>;</b>" <br/><b>|</b> <b>throw</b> "<b>;</b>" <br/><b>|</b> <b>return</b> "<b>;</b>" <br/><b>|</b> <b>return</b> <i> assign_target </i> "<b>;</b>" <br/><b>|</b> <i> error_stmt </i> </dd>
<dt><i>error_stmt</i> &rarr;</dt>
<dd>
 <b>error</b> "<b>;</b>" <br/><b>|</b> <b>error</b> <i> bracketed_string_literal </i> "<b>;</b>" </dd>
<dt><i>statement_except_hashif</i> &rarr;</dt>
<dd>
 <i> warning_stmt </i> </dd>
<dt><i>warning_stmt</i> &rarr;</dt>
<dd>
 <b>_warning</b> <i> bracketed_string_literal </i> "<b>;</b>" </dd>
<dt><i>log_args</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> log_args </i> "<b>,</b>" <i> expression </i> </dd>
<dt><i>compound_statement</i> &rarr;</dt>
<dd>
 "<b>{</b>" <i> statement_list </i> "<b>}</b>" </dd>
<dt><i>statement_list</i> &rarr;</dt>
<dd>
 &lt;empty&gt; <br/><b>|</b> <i> statement_list </i> <i> statement </i> </dd>
<dt><i>local_keyword</i> &rarr;</dt>
<dd>
 <b>local</b> </dd>
<dt><i>static</i> &rarr;</dt>
<dd>
 <b>session</b> </dd>
<dt><i>local</i> &rarr;</dt>
<dd>
 <i> local_keyword </i> <i> cdecl </i> <br/><b>|</b> <i> static </i> <i> cdecl </i> <br/><b>|</b> <i> local_keyword </i> <i> cdecl </i> "<b>=</b>" <i> initializer </i> <br/><b>|</b> <i> static </i> <i> cdecl </i> "<b>=</b>" <i> initializer </i> </dd>
<dt><i>objident_list</i> &rarr;</dt>
<dd>
 <i> objident </i> <br/><b>|</b> <i> objident_list </i> "<b>,</b>" <i> objident </i> </dd>
<dt><i>objident</i> &rarr;</dt>
<dd>
 <i> ident </i> <br/><b>|</b> <b>register</b> </dd>
<dt><i>ident</i> &rarr;</dt>
<dd>
 <b>attribute</b> <br/><b>|</b> <b>bank</b> <br/><b>|</b> <b>bitorder</b> <br/><b>|</b> <b>connect</b> <br/><b>|</b> <b>constant</b> <br/><b>|</b> <b>data</b> <br/><b>|</b> <b>device</b> <br/><b>|</b> <b>event</b> <br/><b>|</b> <b>field</b> <br/><b>|</b> <b>footer</b> <br/><b>|</b> <b>group</b> <br/><b>|</b> <b>header</b> <br/><b>|</b> <b>implement</b> <br/><b>|</b> <b>import</b> <br/><b>|</b> <b>interface</b> <br/><b>|</b> <b>loggroup</b> <br/><b>|</b> <b>method</b> <br/><b>|</b> <b>port</b> <br/><b>|</b> <b>size</b> <br/><b>|</b> <b>subdevice</b> <br/><b>|</b> <b>nothrow</b> <br/><b>|</b> <b>then</b> <br/><b>|</b> <b>throws</b> <br/><b>|</b> <b>_header</b> <br/><b>|</b> <b>param</b> <br/><b>|</b> <b>saved</b> <br/><b>|</b> <i>identifier</i> <br/><b>|</b> <b>class</b> <br/><b>|</b> <b>enum</b> <br/><b>|</b> <b>namespace</b> <br/><b>|</b> <b>private</b> <br/><b>|</b> <b>protected</b> <br/><b>|</b> <b>public</b> <br/><b>|</b> <b>restrict</b> <br/><b>|</b> <b>union</b> <br/><b>|</b> <b>using</b> <br/><b>|</b> <b>virtual</b> <br/><b>|</b> <b>volatile</b> <br/><b>|</b> <b>call</b> <br/><b>|</b> <b>auto</b> <br/><b>|</b> <b>static</b> <br/><b>|</b> <b>select</b> <br/><b>|</b> <b>async</b> <br/><b>|</b> <b>await</b> <br/><b>|</b> <b>with</b> </dd>
</dl>
