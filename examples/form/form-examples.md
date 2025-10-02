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
    <form_heading>
    <marker>14.</marker>Transport Information
    </form_heading>
    <form>
        <form_heading>Land transport ... (Germany)</form_heading>
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
        <form_heading>Sea transport IMDG</form_heading>
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
    <form_heading>Information about you</form_heading>
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
    <form_heading>Information About Your Address</form_heading>
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

![form-07](./form_07.png)

```xml
<heading level="1">SEZIONE II A - REDDITI SOGGETTI A IMPOSTA SOSTITUTIVA</heading>
<form>
    <form_heading level="1">M31</form_heading>
    <form_heading level="2">REDDITI DI CAPITALE SOGGETTI AD IMPOSIZIONE SOSTITUTIVA</form_heading>
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

    <form_heading level="1">M32</form_heading>
    <form_heading level="2">PROVENTI DELLE OBBLIGAZIONI NON ASSOGGETTATI A IMPOSTA SOSTITUTIVA</form_heading>
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

    <form_heading level="1">M33</form_heading>
    <form_heading level="2">PROVENTI DERIVANTI DA DEPOSITI IN GARANZIA</form_heading>
    <form_item>
        <marker>1</marker>
        <key>Ammontare reddito</key>
        <value></value>
    </form_item>
    ...
    
</form>
```

## Example 5

![form-08](./form_08.png)

```xml
<heading level="1">QUADRO W - Investimenti e attività estere di natura finanziaria o patrimoniale</heading>
<heading level="2">SEZIONE I - DATI RELATIVI AGLI INVESTIMENTI E ALLE ATTIVITA'</heading>
<form>
    <form_heading level="1">W1</form_heading>
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

    <form_heading level="1">W2</form_heading>
    <form_item>
        <marker>1</marker>
        <value></value>
    </form_item>
    <form_item>
        <marker>2</marker>
        <value></value>
    </form_item>
    <form_item>
        <marker>3</marker>
        <value></value>
    </form_item>
    ...

</form>
```

## Example 6

![form-09](./form_09.png)
Lower section of a form with fillable fields, markers, hints.
```xml
<heading level="1">QUADRO C - Redditi di lavoro dipendente e assimilati</heading>

<form>
    <form_heading level="1">SEZIONE I - REDDITI DI LAVORO DIPENDENTE E ASSIMILATI</form_heading>
    <form_item>
        <key>Casi particolari</key>
        <checkbox selected="false"></checkbox>
        <key>Codice Stato estero</key>
        <value></value>
    </form_item>

    <form_heading level="2">C1</form_heading>
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

    <form_heading level="2">C2</form_heading>
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

    <form_heading level="2">C3</form_heading>
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
   

    <form_heading level="2">C4</form_heading>
    <form_heading level="3">SOMME PER PREMI DI RISULTATO E WELFARE AZIENDALE</form_heading>
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

## Example 7

![form-19](./form_19_water_damage.png)
Middle section of a form with A and B choices:
```xml
...
<form>
    <form_heading>COCHER LES CASES CONCERNEES</form_heading>
    <form_item>
        <key>La cause du sinistre se situe-t-elle chez vous ?</key>
        <checkbox selected="false"><marker>A</marker>oui</checkbox>
        <checkbox selected="false"><marker>A</marker>non</checkbox>
        <checkbox selected="false"><marker>B</marker>oui</checkbox>
        <checkbox selected="false"><marker>B</marker>non</checkbox>
    </form_item>
    <form_item>
        <key>Êtes-vous assuré en dégâts des eaux ?</key>
        <checkbox selected="false"><marker>A</marker>oui</checkbox>
        <checkbox selected="false"><marker>A</marker>non</checkbox>
        <checkbox selected="false"><marker>B</marker>oui</checkbox>
        <checkbox selected="false"><marker>B</marker>non</checkbox>
    </form_item>
    <form_item>
        <key>Si vous êtes occupant et que vous allez déménager avez-vous donné ou reçu congé ?</key>
        <checkbox selected="false"><marker>A</marker>avant le sinistre</checkbox>
        <checkbox selected="false"><marker>A</marker>après le sinistre</checkbox>
        <checkbox selected="false"><marker>B</marker>avant le sinistre</checkbox>
        <checkbox selected="false"><marker>B</marker>après le sinistre</checkbox>
    </form_item>
    <form_heading>NATURE DES DOMMAGES peinture et/ou papier peint</form_heading>
    <form_item>
        <key>revêtements (sol, mur, plafond)</key>
        <checkbox selected="false"><marker>A</marker>collés</checkbox>
        <checkbox selected="false"><marker>A</marker>agrafés ou cloués</checkbox>
        <checkbox selected="false"><marker>B</marker>collés</checkbox>
        <checkbox selected="false"><marker>B</marker>agrafés ou cloués</checkbox>
    </form_item>
    <form_item>
        <key>Ces aménagements ont-ils été exécutés à vos frais ?</key>
        <checkbox selected="false"><marker>A</marker>oui</checkbox>
        <checkbox selected="false"><marker>A</marker>non</checkbox>
        <checkbox selected="false"><marker>B</marker>oui</checkbox>
        <checkbox selected="false"><marker>B</marker>non</checkbox>
    </form_item>
    <form_item>
        <key>Autres dommages immobiliers (carrelage, parquet, plâtrerie...)</key>
        <checkbox selected="false"><marker>A</marker></checkbox>
        <checkbox selected="false"><marker>B</marker></checkbox>
    </form_item>
    <form_item>
        <key>Objets mobiliers</key>
        <checkbox selected="false"><marker>A</marker></checkbox>
        <checkbox selected="false"><marker>B</marker></checkbox>
    </form_item>
    <form_item>
        <key>Matériels ou marchandises</key>
        <checkbox selected="false"><marker>A</marker></checkbox>
        <checkbox selected="false"><marker>B</marker></checkbox>
    </form_item>
    <form_item>
        <key>Autres dommages</key>
        <value><marker>A</marker><hint>(à préciser)</hint></value>
        <value><marker>B</marker><hint>(à préciser)</hint></value>
    </form_item>
</form>
...
```




















