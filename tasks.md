# Oblig 4, DAT107, GRuppe []

**Gruppenummer:** 

---

## Oppgave 4.1 a - XML Dokument

Filnavn: `lokallag.xml`

Dette dokumentet representerer et lokallag med informasjon om leder, tre medlemmer og deres betalingshistorikk.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<lokallag xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:noNamespaceSchemaLocation="lokallag.xsd">
    <lagnavn>Bergen Kodeklubb</lagnavn>
    <motelokale>
        <gateadresse>Lars Hilles gate 30</gateadresse>
        <postnummer>5008</postnummer>
        <poststed>Bergen</poststed>
    </motelokale>
    <leder>
        <navn>Lise Lotte</navn>
        <mld>101</mld>
    </leder>
    <medlemmer>
        <medlem mld="201">
            <navn>
                <fornavn>Ola</fornavn>
                <etternavn>Nordmann</etternavn>
            </navn>
            <kontaktinfo>
                <telefon>99887766</telefon>
                <epost>ola@test.no</epost>
            </kontaktinfo>
            <adresse>
                <gateadresse>Storgata 1</gateadresse>
                <postnummer>5003</postnummer>
                <poststed>Bergen</poststed>
            </adresse>
            <status>aktiv</status>
            <medlemsavgifter>
                <avgift ar="2024" betalt="ja" betalingsdato="2024-02-01"/>
                <avgift ar="2025" betalt="ja" betalingsdato="2025-01-15"/>
                <avgift ar="2026" betalt="nei"/>
            </medlemsavgifter>
        </medlem>
        <medlem mld="202">
            <navn>
                <fornavn>Kari</fornavn>
                <etternavn>Nordmann</etternavn>
            </navn>
            <kontaktinfo>
                <telefon>44556677</telefon>
                <epost>kari@test.no</epost>
            </kontaktinfo>
            <adresse>
                <gateadresse>Fjellveien 2</gateadresse>
                <postnummer>5014</postnummer>
                <poststed>Bergen</poststed>
            </adresse>
            <status>aktiv</status>
            <medlemsavgifter>
                <avgift ar="2024" betalt="ja" betalingsdato="2024-03-10"/>
                <avgift ar="2025" betalt="ja" betalingsdato="2025-02-20"/>
                <avgift ar="2026" betalt="ja" betalingsdato="2026-01-05"/>
            </medlemsavgifter>
        </medlem>
        <medlem mld="203">
            <navn>
                <fornavn>Per</fornavn>
                <etternavn>Person</etternavn>
            </navn>
            <kontaktinfo>
                <telefon>11223344</telefon>
                <epost>per@test.no</epost>
            </kontaktinfo>
            <adresse>
                <gateadresse>Parkveien 10</gateadresse>
                <postnummer>5007</postnummer>
                <poststed>Bergen</poststed>
            </adresse>
            <status>inaktiv</status>
            <medlemsavgifter>
                <avgift ar="2024" betalt="nei"/>
                <avgift ar="2025" betalt="nei"/>
                <avgift ar="2026" betalt="nei"/>
            </medlemsavgifter>
        </medlem>
    </medlemmer>
</lokallag>
```

---

## Oppgave 4.1 b - XML Skjema

Filnavn: `lokallag.xsd`

Skjemaet sikrer riktig struktur, at postnummer er 4 siffer, og at årstall er mellom 1900 og 2100.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="lokallag">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="lagnavn" type="xs:string"/>
                <xs:element name="motelokale">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="gateadresse" type="xs:string"/>
                            <xs:element name="postnummer">
                                <xs:simpleType>
                                    <xs:restriction base="xs:string">
                                        <xs:pattern value="\d{4}"/>
                                    </xs:restriction>
                                </xs:simpleType>
                            </xs:element>
                            <xs:element name="poststed" type="xs:string"/>
                        </xs:sequence>
                    </xs:complexType>
                </xs:element>
                <xs:element name="leder">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="navn" type="xs:string"/>
                            <xs:element name="mld" type="xs:integer"/>
                        </xs:sequence>
                    </xs:complexType>
                </xs:element>
                <xs:element name="medlemmer">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="medlem" maxOccurs="unbounded">
                                <xs:complexType>
                                    <xs:sequence>
                                        <xs:element name="navn">
                                            <xs:complexType>
                                                <xs:sequence>
                                                    <xs:element name="fornavn" type="xs:string"/>
                                                    <xs:element name="etternavn" type="xs:string"/>
                                                </xs:sequence>
                                            </xs:complexType>
                                        </xs:element>
                                        <xs:element name="kontaktinfo">
                                            <xs:complexType>
                                                <xs:sequence>
                                                    <xs:element name="telefon" type="xs:string" minOccurs="0"/>
                                                    <xs:element name="epost" type="xs:string" minOccurs="0"/>
                                                </xs:sequence>
                                            </xs:complexType>
                                        </xs:element>
                                        <xs:element name="adresse">
                                            <xs:complexType>
                                                <xs:sequence>
                                                    <xs:element name="gateadresse" type="xs:string"/>
                                                    <xs:element name="postnummer">
                                                        <xs:simpleType>
                                                            <xs:restriction base="xs:string">
                                                                <xs:pattern value="\d{4}"/>
                                                            </xs:restriction>
                                                        </xs:simpleType>
                                                    </xs:element>
                                                    <xs:element name="poststed" type="xs:string"/>
                                                </xs:sequence>
                                            </xs:complexType>
                                        </xs:element>
                                        <xs:element name="status" type="xs:string"/>
                                        <xs:element name="medlemsavgifter">
                                            <xs:complexType>
                                                <xs:sequence>
                                                    <xs:element name="avgift" maxOccurs="unbounded">
                                                        <xs:complexType>
                                                            <xs:attribute name="ar" use="required">
                                                                <xs:simpleType>
                                                                    <xs:restriction base="xs:integer">
                                                                        <xs:minInclusive value="1900"/>
                                                                        <xs:maxInclusive value="2100"/>
                                                                    </xs:restriction>
                                                                </xs:simpleType>
                                                            </xs:attribute>
                                                            <xs:attribute name="betalt" type="xs:string" use="required"/>
                                                            <xs:attribute name="betalingsdato" type="xs:date" use="optional"/>
                                                        </xs:complexType>
                                                    </xs:element>
                                                </xs:sequence>
                                            </xs:complexType>
                                        </xs:element>
                                    </xs:sequence>
                                    <xs:attribute name="mld" type="xs:integer" use="required"/>
                                </xs:complexType>
                            </xs:element>
                        </xs:sequence>
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
        <xs:unique name="uniqueMld">
            <xs:selector xpath="medlemmer/medlem"/>
            <xs:field xpath="@mld"/>
        </xs:unique>
    </xs:element>
</xs:schema>
```

---

## Oppgave 4.1 c - PostgreSQL XML Spørring

```sql
SELECT xmlelement(name "aktive-medlemmer",
    xmlagg(
        xmlelement(name "medlem",
            xmlattributes(m.medlemsnummer as "mld"),
            xmlelement(name "fornavn", m.fornavn),
            xmlelement(name "etternavn", m.etternavn),
            (SELECT xmlelement(name "avgift-2026", 
                xmlattributes(
                    ma.betalt as "betalt",
                    CASE WHEN ma.betalt = 'J' THEN ma.betalingsdato ELSE NULL END as "betalingsdato"
                )
            )
            FROM medlemsavgift ma 
            WHERE ma.medlemsnummer = m.medlemsnummer 
            AND ma.ar = EXTRACT(YEAR FROM CURRENT_DATE))
        )
    )
)
FROM medlem m
WHERE m.aktiv = 'J' AND m.lokallag_id = 1;
```

---

## Oppgave 4.2 a - JSON Dokument

Filnavn: `lokallag.json`

```json
{
  "lagnavn": "Bergen Kodeklubb",
  "motelokale": {
    "gateadresse": "Lars Hilles gate 30",
    "postnummer": "5008",
    "poststed": "Bergen"
  },
  "leder": {
    "navn": "Lise Lotte",
    "mld": 101
  },
  "medlemmer": [
    {
      "mld": 201,
      "navn": { "fornavn": "Ola", "etternavn": "Nordmann" },
      "kontaktinfo": { "telefon": "99887766", "epost": "ola@test.no" },
      "adresse": { "gateadresse": "Storgata 1", "postnummer": "5003", "poststed": "Bergen" },
      "status": "aktiv",
      "medlemsavgifter": [
        { "ar": 2024, "betalt": "J", "betalingsdato": "2024-02-01" },
        { "ar": 2025, "betalt": "J", "betalingsdato": "2025-01-15" },
        { "ar": 2026, "betalt": "N" }
      ]
    }
  ]
}
```

---

## Oppgave 4.2 b - PostgreSQL JSON Spørring

```sql
SELECT json_build_object(
    'aktive-medlemmer', json_agg(
        json_build_object(
            'mld', m.medlemsnummer,
            'fornavn', m.fornavn,
            'etternavn', m.etternavn,
            'avgift_status', (
                SELECT json_build_object(
                    'betalt', ma.betalt,
                    'betalingsdato', CASE WHEN ma.betalt = 'J' THEN ma.betalingsdato ELSE NULL END
                )
                FROM medlemsavgift ma
                WHERE ma.medlemsnummer = m.medlemsnummer
                AND ma.ar = EXTRACT(YEAR FROM CURRENT_DATE)
            )
        )
    )
)
FROM medlem m
WHERE m.aktiv = 'J' AND m.lokallag_id = 1;
```

---

## Oppgave 4.3 a - Valg av NoSQL

Jeg ville valgt **MongoDB**.
**Begrunnelse:** MongoDB er en dokumentorientert database som er svært velegnet for denne typen applikasjon. Den støtter nøstede objekter, noe som gjør det enkelt å lagre påmeldinger direkte inne i et arrangement eller medlemsavgifter inne i et medlem.

* **Redis** er en nøkkel-verdi database som er for enkel for komplekse spørringer.
* **Cassandra** er laget for enorme datamengder og høy skalerbarhet, men er mindre fleksibel på datamodellering enn MongoDB.
* **Neo4j** er en grafdatabase, som er bra for relasjoner, men kanskje unødvendig komplisert for en enkel påmeldingsløsning.

## Oppgave 4.3 b - Datamodell (MongoDB)

Jeg velger å bruke **Embedding** for påmeldinger. Hvert dokument i samlingen `arrangementer` inneholder en liste over påmeldte medlemmer.
**Begrunnelse:** Dette gjør at vi kan hente all informasjon om et arrangement og hvem som er påmeldt i én enkelt leseoperasjon, noe som gir god ytelse for en web-løsning.

## Oppgave 4.3 c - Eksempeldata

```javascript
db.arrangementer.insertMany([
  {
    tittel: "Sommerfest 2026",
    dato: "2026-06-20",
    sted: "Bergen Park",
    pameldinger: [
      { medlemsnummer: 201, navn: "Ola Nordmann", dato: "2026-05-01" },
      { medlemsnummer: 202, navn: "Kari Nordmann", dato: "2026-05-02" },
      { medlemsnummer: 204, navn: "Siri S", dato: "2026-05-03" }
    ]
  },
  {
    tittel: "Workshop: MongoDB",
    dato: "2026-09-15",
    sted: "HVL Campus",
    pameldinger: [
      { medlemsnummer: 201, navn: "Ola Nordmann", dato: "2026-08-01" },
      { medlemsnummer: 205, navn: "Arne A", dato: "2026-08-05" },
      { medlemsnummer: 206, navn: "Berit B", dato: "2026-08-10" }
    ]
  }
]);
```

---

## Oppgave 4.4 - MongoDB Query API

* **a)** `db.medlem.insertOne({_id: 100, fornavn: "Jan", etternavn: "Jansen", lokallag_id: 1, aktiv: "J"});`
* **b)** `db.lokallag.insertMany([{_id: 2, lagnavn: "Oslo"}, {_id: 3, lagnavn: "Trondheim"}]);`
* **c)** `db.lokallag.deleteOne({_id: 3});`
* **d)** `db.lokallag.find();`
* **e)** `db.medlem.find({lokallag_id: 1});`
* **f)** `db.medlem.find({lokallag_id: 1}).sort({_id: 1}).limit(3);`
* **g)** `db.medlem.find({poststed: "Bergen"});`
* **h)** `db.medlem.find({aktiv: "J", medlemsavgifter: {$elemMatch: {ar: 2025, betalt: "J"}}});`
* **i)** `db.medlem.find({$or: [{fornavn: /^A/}, {etternavn: /^J/}]});`
* **j)** `db.medlem.countDocuments({lokallag_id: 1});`
* **k)** `db.medlem.aggregate([{$group: {_id: "$lokallag_id", antall: {$sum: 1}}}]);`
* **l)** `db.medlem.updateMany({lokallag_id: 1}, {$push: {medlemsavgifter: {ar: 2027, betalt: "N"}}});`