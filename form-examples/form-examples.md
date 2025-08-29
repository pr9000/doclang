# Form Examples

## Example 0

![form-00](./from_00.png)

```xml
<form>
    <form_item>
        <key>Firma:</key>
        <value>Holcim ... GmbH</value>
    </form_item>
    <form_item>
        <key>Werk:</key>
        <value>Scholkholz</value>
    </form_item>
    ...
    <form_item>
        <key>Petrograph. Typ:</key>
        <value>Quartiarer Sand + Kies</value>
    </form_item>
</form>
```

## Example 1

![form-01](./from_01.png)

```xml
<form>
    <form_header>
    <marker>14.</marker>Transport Information
    </form_header>
    <form>
        <form_header>Land transport ... (Germany)</form_header>
        <form_item>
            <key>GGVS/GGVE class:</key>
            <value>8</value>
        </form_item>
        <form_item>
            <key>ADR/RID class:</key>
            <value>8</value>
        </form_item>
        ...
    </form>
    <form_item>
        <key>River transport ADN/ADNR</key>
        <value>not examined</value>
    </form_item>
    <form>
        <form_header>Sea transport IMDG</form_header>
        ...
    </form>
    ...
    <text>The transport ... considered.</text>
    <text>THESE TRANSPORT ... PACK!</text>    
</form>
```

## Example 2

![form-02](./from_02.png)

```xml
<form>
    <form_item>
        <key>Description</key>
        <value>A.A. Cat</value>
    </form_item>
    <form_item>
        <key>Quant.</key>
        <value></value>
    </form_item>
        <form_item>
        <key>Un</key>
        <value></value>
    </form_item>
    <form_item>
        <key>Measure</key>
        <value></value>
    </form_item>
    <form_item>
        <key>Price (in currency)</key>
        <value></value>
    </form_item>
    <form_item>
        <key>Un</key>
        <value></value>
    </form_item>
    <form_item>
        <key>Total</key>
        <value></value>
    </form_item>
    <text></text>
    <form>
        <form_item>
            <key>Delivery Cost</key>
            <value></value>
        </form_item>
        <form_item>
            <key>Maintenance</key>
            <value></value>
        </form_item>
        ...
    <form>
    <form>
        <form_item>
            <key>Date and time of delivery:</key>
            <value></value>
        </form_item>
        ...
        <form_item>
            <key>Guarantee</key>
            <value></value>
        </form_item>
        <text>Delivery Supplies ... Finance Department</text>
    </form>
    ...
</form>
```

## Example 3

![form-03](./from_03.png)

```xml
<form>
    <form_header>Information about you</form_header>
    <form_item>
        <key>*Family Name (Last Name)</key>
        <value>staar</value>
    </form_item>
    <form_item>
        <key>*Given Name (First Name)</key>
        <value>peter</value>
    </form_item>
    <form_item>
        <key>*Middle Name (if applicable)</key>
        <value>WJ</value>
    </form_item>
    <form_item>
        <key>I am in the United States as a:</key>
        <checkbox selected="false">Visitor</checkbox>
        <checkbox selected="false">Student</checkbox>
        <checkbox selected="false">Permanent Resident</checkbox>
        <checkbox selected="false">Other (Specify)</checkbox>
        <text></text>
    <form_item>
    <form_item>
        <key>Country of Citizenship</key>
        <value></value>
    </form_item>
    <form_item>
        <key>*Date of Birth</key>
        <value></value>
    </form_item>
    <form_item>
        <key>Alien Registration Number (A-Number) (if any)</key>
        <value></value>
    </form_item>
    <form_header>Information About Your Address</form_header>
    <text>*Present Physical Address ()No Po Boxes</text>
    <form_item>
        <key>*Street ... Name</key>
        <value></value>
    </form_item>
    <form_item>
        <key>Apt.</key>
        <checkbox selected="false"></checkbox>
    </form_item>
    <form_item>
        <key>Ste.</key>
        <checkbox selected="false"></checkbox>
    </form_item>
    ...
    
</form>
```

