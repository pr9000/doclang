# Form Examples

## Example 0

![form-00](./form_00.png)

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

![form-01](./form_01.png)

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

![form-02](./form_02.png)

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

![form-03](./form_03.png)

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

## Example 4

![form-03](./form_07.png)

```xml
<section_header_1>SEZIONE II A - REDDITI SOGGETTI A IMPOSTA SOSTITUTIVA</section_header_1>
<form>
    <form_header_1>M31</form_header_1>
    <form_header_2>REDDITI DI CAPITALE SOGGETTI AD IMPOSIZIONE SOSTITUTIVA</form_header_2>
    <form_item>
    	 <marker>1</marker>
        <key>Tipo</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>2</marker>
        <key>Codice Stato estero</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>3</marker>
        <key>Ammontare reddito</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>4</marker>
        <key>Aliquota %</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>5</marker>
        <key>Credito IVCA</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>6</marker>
        <key>Proventi particolari</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>7</marker>
        <key>Opzione tassazione ordinaria</key>
        <value></value>
    </form_item>

    <form_header_1>M32</form_header_1>
    <form_header_2>PROVENTI DELLE OBBLIGAZIONI NON ASSOGGETTATI A IMPOSTA SOSTITUTIVA</form_header_2>
    <form_item>
        <marker>1</marker>
        <key>Ammontare reddito</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>2</marker>
        <key>Aliquota %</key>
        <value></value>
    </form_item>

    <form_header_1>M33</form_header_1>
    <form_header_2>PROVENTI DERIVANTI DA DEPOSITI IN GARANZIA</form_header_2>
    <form_item>
        <marker>1</marker>
        <key>Ammontare reddito</key>
        <value></value>
    </form_item>
    ...
    
</form>
```

## Example 5

![form-03](./form_08.png)

```xml
<section_header_1>QUADRO W - Investimenti e attività estere di natura finanziaria o patrimoniale</section_header_1>
<section_header_2>SEZIONE I - DATI RELATIVI AGLI INVESTIMENTI E ALLE ATTIVITA'</section_header_2>
<form>
    <form_header_1>W1</form_header_1>
    <form_item>
        <marker>1</marker>
        <key>CODICE TITOLO POSSESSO</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>2</marker>
        <key>TIPO CONTRIBUENTE - IVAFE</key>
        <value></value>
    </form_item>
    ...

    <form_header_1>W2</form_header_1>
    <form_item>
        <marker>1</marker>
        <value></value>
    </form_item>
    <form_item>
        <marker>2</marker>
        <value></value>    </form_item>
    <form_item>
        <marker>3</marker>
        <value></value>
    </form_item>
    ...

</form>
```

## Example 6

![form-03](./form_09.png)

```xml
<section_header_1>QUADRO C - Redditi di lavoro dipendente e assimilati</section_header_1>
<section_header_2>SEZIONE I - REDDITI DI LAVORO DIPENDENTE E ASSIMILATI</section_header_2>
<text>Casi particolari</text>
<text>Codice Stato estero</text>

<form>
    <form_header_1>C1</form_header_1>
    <form_item>
        <marker>1</marker>
        <key>TIPO</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>2</marker>
        <key>INDETERMINATO/DETERMINATO</key>
        <checkbox selected="false"></checkbox>
    </form_item>
    <form_item>
        <marker>3</marker>
        <key>REDDITO (punti 1,2,3 CU 2025)</key>
        <value>,00</value>
    </form_item>
    <form_item>
        <marker>4</marker>
        <key>ALTRI DATI</key>
        <checkbox selected="false"></checkbox>
    </form_item>

    <form_header_1>C2</form_header_1>
    <form_item>
        <marker>1</marker>
        <key>TIPO</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>2</marker>
        <key>INDETERMINATO/DETERMINATO</key>
        <checkbox selected="false"></checkbox>
    </form_item>
    <form_item>
        <marker>3</marker>
        <key>REDDITO (punti 1,2,3 CU 2025)</key>
        <value>,00</value>
    </form_item>
    <form_item>
        <marker>4</marker>
        <key>ALTRI DATI</key>
        <checkbox selected="false"></checkbox>
    </form_item>

    <form_header_1>C3</form_header_1>
    <form_item>
        <marker>1</marker>
        <key>TIPO</key>
        <value></value>
    </form_item>
    <form_item>
        <marker>2</marker>
        <key>INDETERMINATO/DETERMINATO</key>
        <checkbox selected="false"></checkbox>
    </form_item>
    <form_item>
        <marker>3</marker>
        <key>REDDITO (punti 1,2,3 CU 2025)</key>
        <value>,00</value>
    </form_item>
    <form_item>
        <marker>4</marker>
        <key>ALTRI DATI</key>
        <checkbox selected="false"></checkbox>
    </form_item>
   

    <form_header_1>C4</form_header_1>
    <form_header_2>SOMME PER PREMI DI RISULTATO E WELFARE AZIENDALE</form_header_2>
    <form_item>
        <marker>1</marker>
        <key>TIPOLOGIA LIMITE</key>
        <checkbox selected="false"></checkbox>
    </form_item>
    <form_item>
        <marker>2</marker>
        <key>SOMME A TASSAZIONE ORDINARIA</key>
        <value>,00</value>
    </form_item>
    <form_item>
        <marker>3</marker>
        <key>SOMME A IMPOSTA SOSTITUTIVA</key>
        <value>,00</value>
    </form_item>
    ...

</form>
```























