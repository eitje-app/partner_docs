# Automatically sync revenue

## Authentication
Before you can do anything, the customer has to obtain his API-key & login name in eitje. You can find it under 'Settings' > 'Company settings' > 'Revenue integration'. After the customer has done all this, we can start the synchronization of revenue groups.


These paramaters are mandatory for every call, otherwise we can't authorize your application:

```
env_name: string,
revenue_key string,
```

## Synchronizing revenue groups

Endpoint:

```
POST /partners/revenue_groups
```

Parameters:

```

groups: [{
	name: string,
	id: (string|number),
	
}],
cash_registers: [{
	name: string,
	id: (string|number),
}]
```

> The ID is crucial for the integration because we use it to sync the revenue groups from your system to those in our system. Make sure this field is unique & never changes. Its type can be a string or a number, that's up to you. The name can change without any difficulties, as it's only used to make it easier for customers in the eitje UI. Both the groups & cash registers paramaters are mandatory, if you don't provide at least one of both, the request will fail.








## Uploading revenue

> Before you can do this, the customer first has to have linked the revenue groups in eitje. 

Endpoint:

```
POST /partners/revenue
```

Parameters:

```
cash_registers: [{
	id: (string|number),
	revenue_groups: [
		{id: (string|number), amount_in_cents: number},
	],
}],
date: string(DD/MM/YYYY || YYYY/MM/DD)

```

> Pay attention that you always report the revenue in CENTS, and that you use the correct date format. 

> Another important note is that you should always send data from all cash registers, because we expect the total of the day, and reset the revenue values on every call. This also means that if you've made a mistake you can easily re-run the call without issues ;)