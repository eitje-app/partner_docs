# Automatisch omzet inschieten

## Authenticatie
Voordat je iets kan doen, moet de klant in eitje zijn omzet API-key & inlognaam vinden en die in jouw systeem invoeren. In eitje is dit te vinden onder 'bedrijf' en vervolgens 'omzetkoppeling'. Zodra de klant dit heeft gedaan, kunnen we beginnen met het synchroniseren van de omzetgroepen.

Bij elke call zijn de volgende paramaters dan ook verplicht, anders krijg je een 401:

```
env_name: string,
revenue_key string,
```

## Synchroniseren van omzetgroepen

Endpoint:

```
POST /partners/revenue_groups
```

Parameters:

```

groups: {
	name: string,
	id: (string|number)
}
```

> Het ID is cruciaal: daarmee gaan wij de koppeling maken tussen de omzetgroepen, dus zorg dat dit een uniek veld is en dat het onveranderlijk is. Je mag zelf bepalen of het een string of number is. De naam kan wel veranderen zonder gevolgen, die wordt gebruikt om de klant in eitje makkelijk de groepen te laten koppelen.







## Doorzetten van omzet

> Voordat je dit kan doen, moet de klant eerst in eitje de omzetgroepen aan elkaar koppelen.

Endpoint:

```
POST /partners/revenue
```

Parameters:

```
groups: {
	id: (string|number),
	amount_in_cents: number,
},
date: string, format: (DD/MM/YYYY OR YYYY/MM/DD)

```

> Let er op dat het bedrag in centen moet worden ingeschoten en dat je het juiste datumformat aanhoudt. 

