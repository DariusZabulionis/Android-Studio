# Fragmentai

[https://developer.android.com/guide/fragments](https://developer.android.com/guide/fragments)

[https://developer.android.com/guide/fragments/fragmentmanager](https://developer.android.com/guide/fragments/fragmentmanager)

Fragmentas – tai pakartotinai naudojama jūsų programos vartotojo sąsajos dalis. Fragmentas apibrėžia ir valdo savo išdėstymą, turi savo gyvavimo ciklą ir gali apdoroti savo įvesties įvykius. Fragmentai negali veikti savarankiškai. Juos turi talpinti veikla arba kitas fragmentas. Fragmento vaizdų hierarchija tampa talpinančio elemento vaizdų hierarchijos dalimi arba prie jos prisijungia.

## Moduliarumas

Fragmentai suteikia jūsų veiklos vartotojo sąsajai moduliarumą ir pakartotinį naudojimą, leidžiant suskirstyti sąsają į atskiras dalis. Veiklos yra ideali vieta, kur galima įdėti bendruosius elementus, pavyzdžiui, navigacijos meniu, visoje programos vartotojo sąsajoje. Kita vertus, fragmentai labiau tinka apibrėžti ir valdyti vieno ekrano arba ekrano dalies vartotojo sąsają.

Įsivaizduokite programėlę, kuri prisitaiko prie įvairių ekrano dydžių. Didesniuose ekranuose galbūt norėsite, kad programėlė rodytų statinį navigacijos meniu ir sąrašą, išdėstytą tinkleliu. Mažesniuose ekranuose galbūt norėsite, kad programėlė rodytų apatinę navigacijos juostą ir sąrašą, išdėstytą linijiniu būdu.

Šių variantų valdymas veikloje yra sudėtingas. Atskyrus navigacijos elementus nuo turinio, šį procesą galima padaryti lengviau valdomą. Tuomet veikla yra atsakinga už teisingos navigacijos vartotojo sąsajos rodymą, o fragmentas rodo sąrašą su tinkamu išdėstymu.

<img width="1530" height="902" alt="image" src="https://github.com/user-attachments/assets/e291a000-71d7-4ff7-86a6-fac0c6bb9dfb" />


1 Pav. Dvi to paties ekrano versijos skirtingų dydžių ekranuose. Kairėje – dideliame ekrane yra navigacijos meniu, kurį valdo veikla, ir tinklelinis sąrašas, kurį valdo fragmentas. Dešinėje – mažame ekrane yra apatinė navigacijos juosta, kurią valdo veikla, ir linijinis sąrašas, kurį valdo fragmentas.


Suskirstydami vartotojo sąsają į fragmentus, galite lengviau keisti veiklos išvaizdą vykdymo metu. Kol veikla yra „STARTED“ gyvavimo ciklo būsenoje arba aukštesnėje, fragmentus galima pridėti, pakeisti arba pašalinti. Be to, šiuos pakeitimus galite įrašyti į veiklos valdomą grįžimo steką, kad vėliau būtų galima juos atšaukti.

Tą pačią fragmento klasę galite naudoti kelis kartus toje pačioje veikloje, keliose veiklose arba net kaip kito fragmento vaiką. Turėdami tai omenyje, suteikite fragmentui tik tą logiką, kuri reikalinga jo pačios vartotojo sąsajos valdymui. Venkite priklausomybės nuo vieno fragmento ar kito fragmento manipuliavimo.


## Fragmento sukūrimas

Fragmentas – tai veiklos viduje esanti modulinė vartotojo sąsajos dalis. Fragmentas turi savo gyvavimo ciklą, gauna savo įvesties įvykius, o fragmentus galima pridėti arba pašalinti tuo metu, kai veikia juos talpinanti veikla.

Šiame dokumente aprašoma, kaip sukurti fragmentą ir įtraukti jį į veiklą.

## Sukurkite savo aplinką

## Create a fragment class

To create a fragment, extend the AndroidX [Fragment](https://developer.android.com/reference/androidx/fragment/app/Fragment) class, and override its methods to insert your app logic, similar to the way you would create an [Activity](https://developer.android.com/reference/android/app/Activity) class. To create a minimal fragment that defines its own layout, provide your fragment's layout resource to the base constructor, as shown in the following example:


java
```java
class ExampleFragment extends Fragment {
    public ExampleFragment() {
        super(R.layout.example_fragment);
    }
}
```

kotlin
```kotlin
class ExampleFragment : Fragment(R.layout.example_fragment)
```

„Fragment“ biblioteka taip pat siūlo specializuotesnes fragmentų bazines klases:

[`DialogFragment`](https://developer.android.com/reference/androidx/fragment/app/DialogFragment)

Rodo plaukiojantį dialogo langą. Šios klasės naudojimas dialogo langui sukurti yra gera alternatyva [Activity](https://developer.android.com/reference/android/app/Activity) klasėje esančių dialogo pagalbinių metodų naudojimui, nes fragmentai automatiškai tvarko dialogo lango sukūrimą ir išvalymą. Daugiau informacijos duota skyriuje [Dialogų rodymas](https://developer.android.com/guide/fragments/dialogs) naudojant [DialogFragment](https://developer.android.com/guide/fragments/dialogs).


[`PreferenceFragmentCompat`](https://developer.android.com/reference/androidx/preference/PreferenceFragmentCompat)


Rodo [Preference](https://developer.android.com/reference/androidx/preference/Preference) objektų hierarchiją sąrašo pavidalu. Naudodami „PreferenceFragmentCompat“ galite sukurti savo programos nustatymų ekraną.

