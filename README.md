###### Tobias Skog .NET23
## Case 1
##### Problem
>Koden genererar ett fel och körs inte.
##### Problem Kod
```C#
int number = 2;

if (number > 3)
{
    Console.WriteLine("Talet är större än tre")
}
elseif(number < 3)
{
    Console.WriteLine("Talet är mindre än tre");
}
```
##### Felbeksrivning
På rad 5 är det ett uteslutet `;` .
På rad 7 så är problemet `elseif` . I C# (och många andra språk) använder vi `else if` . Detta gör så att koden blir lite lättare att läsa.
	Detta hjälper till att göra koden lätt att identifiera efter enbart en kort överblick.
	Om vi jämför  `if ... else if ... else`  med `if ... elseif ... else`
	så är det lättare att se strukturen i det första exemplet.
##### Uppdaterad Kod
```C#
int number = 2;

if (number > 3)
{
    Console.WriteLine("Talet är större än tre");
}
else if(number < 3)
{
    Console.WriteLine("Talet är mindre än tre");
}
```

## Case 2
##### Problem
>Koden ska skriva ut alla siffror mellan 1 och 100 men skriver bara ut till nummer 99
##### Problem Kod
```C#
for(int i=1; i<100; i++)
{
    Console.WriteLine(i);
}
```
##### Felbeksrivning
På rad 1 i våran for loop så börjar vi korrekt med att räkna från 1 upp till `<100`  = 99.
Det vi måste tänka på då vi vill skriva ut den sista siffran i vår for loop är att ändra `<` till `<=`  då ser for loopen ut så här `for(int i = 1; i <= 100; i++)`  Då börjar vi på 1 och fortsätter tills dess att `i` är mindre ELLER likamed 100. dvs sista iterationen av loopen så är `i = 100`, och vi skriver `100` till konsolen.
##### Uppdaterad Kod
```C#
for(int i=1; i<=100; i++)
{
    Console.WriteLine(i);
}
```

## Case 3
##### Problem
>Koden genererar ett fel och körs inte
##### Problem Kod
```C#
for (int i = 1; i <= 5; i)
{
    for (int j = 1; j <= i; j)
    {
        Console.Write(j + " ");
    }
    Console.WriteLine();
}
```
##### Felbeksrivning
På rad 1 i slutet av for loopen har vi glömt att välja vad vi ska göra med vår variable `i`.
På rad 3 har vi samma problem fast med variabeln `j`.
Då vi initiar `i` och `j` till `1`  så antar jag att vi vill inkrementera loopen med `1` efter varje iteration.
Så lösningen blir:
Rad 1 `for (int i = 1; i <= 5; i++)` 
Rad 3 `for (int j = 1; j <= i; j++)` 
Notera att vi la till `++` i slutet av for loopen till vår variabel `i` och `j`.
##### Uppdaterad Kod
```C#
for (int i = 1; i <= 5; i++)
{
    for (int j = 1; j <= i; j++)
    {
        Console.Write(j + " ");
    }
    Console.WriteLine();
}
```

## Case 4
##### Problem
>Koden har ingen output, varför inte?
##### Problem Kod
```C#
int i = 1;
while (i <= 5)
{
	for (int j = 1; j <= i; j++)
	{
		Console.Write();
	}

	Console.WriteLine();
	i++;
}
```
##### Felbeksrivning
På rad 6 använder vi oss av `Console.Write()` , men vi ger inte metoden någon data att skriva.
`Console.Write()` metoden har ingen overload metod där den tar 0 argument, så glömmer vi att ge metoden någon form av data att skriva ut så blir det ett error.
Om vi istället passar in variabeln `j`  så får vi följande output.
```
1
12
123
1234
12345
```
eller om vi följer koden i Case 3 och skriver ut `Console.Write(j + " ");` så får vi följande output
```
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
```
Det andra exemplet ser visuelt bättre ut, så det är lösningen jag kommer att ha i min uppdaterade kod
##### Uppdaterad Kod
```C#
int i = 1;
while (i <= 5)
{
	for (int j = 1; j <= i; j++)
	{
		Console.Write(j + " ");
	}

	Console.WriteLine();
	i++;
}
```


## Case 5
##### Problem
>Eftersom i är 1 i exemplet nedan förväntar vi oss att koden inte ska göra något men nu skriver den ut "Two". Varför blir det så och hur löser vi det så att det inte blir någon utskrift om i är 1?
##### Problem Kod
```C#
int i = 1;

switch (i)
{
    case 1:
    case 2:
        Console.WriteLine("Two");
        break;
    default:
        Console.WriteLine("Other");
        break;
}
```
##### Felbeksrivning
När man använder sig av en `switch` kan man sätta flera alternativ till samma svar genom att sätta flera `case` ´s efter varandra som i koden här ovan så chainar vi `case 1:` och `case 2:` tillsammans och säger OM `i`  är `1` ELLER `2` så gör detta sen `default:` är vad som händer om `i` är allt annat än `1` eller `2` .
I den uppdaterade koden så har vi lagt till 1 rad kod (rad 6). Efter  `case 1:` som också kan läsas som ( `i = 1`)  så avbryter vi switchen med  `break` och skriver inte ut något till konsolen.
##### Uppdaterad Kod
```C#
int i = 1;

switch (i)
{
    case 1:
	    break;
    case 2:
        Console.WriteLine("Two");
        break;
    default:
        Console.WriteLine("Other");
        break;
}
```

## Case 6
##### Problem
>Koden genererar ett fel och körs inte.
##### Problem Kod
```C#
int i = 10;

if(i = 5)
{
    Console.WriteLine("i är 5");
}
```
##### Felbeksrivning
På raid 3 så uttrycker vi oss fel i if satsen.
När vi vill kolla om ett värde är desamma som ett annat använder vi oss av `==`. 
När vi tilldelar ett värde till en variabel använder vi oss av `=`.
##### Uppdaterad Kod
```C#
int i = 10;

if(i == 5)
{
    Console.WriteLine("i är 5");
}
```
