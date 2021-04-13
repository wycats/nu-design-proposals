# Core Expressions

The core expressions are:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Expression</th>
      <th style="text-align:left">Evaluation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>Literal</code>
      </td>
      <td style="text-align:left">Into itself</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Boolean</code>
      </td>
      <td style="text-align:left">
        <p>Into <code>true</code> or <code>false</code>
        </p>
        <p>&#x2139; This should be a <code>Literal</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>ExternalCommandName</code>
      </td>
      <td style="text-align:left">
        <p>Represents the name of an external command.</p>
        <p>&#x2139; This should be a <code>Symbol</code>, perhaps with newtype</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>CommandName</code>
      </td>
      <td style="text-align:left">
        <p>Represents the name of a command.</p>
        <p>&#x2139; This should be a <code>Symbol</code>, perhaps with newtype</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>VariableReference</code>
      </td>
      <td style="text-align:left">The value of the variable in the current scope</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>VariableBinding</code>
      </td>
      <td style="text-align:left">Initialize a variable with a value for the remainder of the scope</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>BinaryExpression</code>
      </td>
      <td style="text-align:left">Determined by the Operator</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Range</code>
      </td>
      <td style="text-align:left">&#x2139; This should be a <code>BinaryExpression</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Block</code>
      </td>
      <td style="text-align:left"><a href="core-expressions.md#block-evaluation">Block Evaluation</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>FunctionLiteral</code>
      </td>
      <td style="text-align:left">A <a href="values/functions.md">Function</a> that can be invoked later</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>ListLiteral</code>
      </td>
      <td style="text-align:left">A <a href="values/collections.md#list">List</a> of values</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>TableLiteral</code>
      </td>
      <td style="text-align:left">A <a href="values/collections.md#table">Table</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>FilePath</code>
      </td>
      <td style="text-align:left">A <a href="values/semantics_primitives.md#filepath">FilePath</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Symbol</code>
      </td>
      <td style="text-align:left">A <a href="values/semantics_primitives.md#symbol">Symbol</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Call</code>
      </td>
      <td style="text-align:left"><a href="core-expressions.md#call-evaluation">Call Evaluation</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Id</code>
      </td>
      <td style="text-align:left"><a href="core-expressions.md#id-evaluation">ID Evaluation</a>
      </td>
    </tr>
  </tbody>
</table>

### Block Evaluation

1. For each expression in the block, evaluate the expression
2. The block evaluates to the value of the final evaluated expression

### Call Evaluation

{% hint style="warning" %}
This needs to be better specified, but it's basically bog-standard call evaluation.
{% endhint %}

### ID Evaluation

An `ID` is backed by a unique `UUID` for every evaluation.

