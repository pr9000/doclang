# Inline Examples

There are a few rules we should follow with inline groups,

1. children of an inline group can only be of type
    - `text`
    - `formula`
    - `code`
2. children of an inline group can not have children
3. children of an inline group can not have location tags
4. inline groups can have location tags
5. text element can have multiple inline children (if split across columns, page, etc)

## Example 0

![inline-00](./inline_00.png)

Each block that has location information is a top-level tag of the corresponding label, e.g. "text".

Top-level tags which belong to the same item should have the same continuation ID.

```xml
<text loc_x0="10" loc_y0="20" loc_x1="30" loc_y1="40" continue_id="1">
    where τ<subscript>x,y,z</subscript> are the Pauli matrices acting
    on Nambu space. We consider a circular-shaped boundary, the nor-
</text>

<caption loc_x0="15" loc_y0="25" loc_x1="35" loc_y1="45">
    FIG. 3. The modules of the inner product of two MES spinors
    <formula>...<formula/>
    ...
</caption>

<text loc_x0="20" loc_y0="30" loc_x1="40" loc_y1="50" continue_id="1">
    mal direction of the boundary tangent for arbitrary angle θ is
    <formula>ˆx⊥ = (cos θ, sin θ)</formula>
    . Next, we assume an ansatz for the edge state wave function at θ as
	<formula>Ψu/l(x⊥) =eλx⊥ eik∥ x∥ ξu/l </formula>
	with
	<formula>k∥ = sin θkx − cos θky</formula>
	Here, |ξu⟩ and |ξl⟩ represent the spinors ...  of the chiral MESs with
	<formula>φu = 0</formula>
    and
	<formula>φl = φ:</formula>
</text>
```
