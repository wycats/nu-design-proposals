# Whitespace

### Separator

A separator indicates that an expression that is eligible for termination should be terminated.

* newline
* `;`
* `,`

{% hint style="info" %}
Separators are processed in the [Reading](phase-1-reading.md) parsing phase.
{% endhint %}

### Whitespace

Any whitespace that is not a [Separator](untitled.md) is generic whitespace.

{% hint style="info" %}
Non-separator whitespace is contextually processed in the [Expanding](phase-2-expanding/) parsing phase.
{% endhint %}

