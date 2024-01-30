Basisprogrammeren voor games is heel specifiek, daarom zal ik alleen de syntax(hoe je functies moet gebruiken, uitleggen)
# Component als variable
Wij moeten vaak Components aanpassen in de code. Denk aan `rigidbody`, Dit zorgt ervoor dat wij vooruit bewegen zonder transform.translate.
```c#
private Rigidbody playerRb;

private void Start()
{
	playerRb = GetComponent<Rigidbody>();
	playerRb.AddForce(Vector3.up * 1000);
}
```
## Jump maken
we willen alleen omhoog gaan als wij bijvoorbeeld op spatie drukken. Dit kunnen wij doen met een if statement.
```c#
if (Input.GetKeyDown(KeyCode.Space))
{
	playerRb.AddForce(Vector3.up * jumpforce, ForceMode.Impulse);
}
```

Als je wil dat hij alleen springt wanneer je op de grond staat, kan je dit gebruiken

```c#
```c#
private bool isOnGround;
if (Input.GetKeyDown(KeyCode.Space) && isOnGround)
{
	playerRb.AddForce(Vector3.up * jumpforce, ForceMode.Impulse);
	isOnGround = false;
}

private void OnCollisionEnter(Collision collision)
{
isOnGround = true;
}
```

# CompareTag en .Find
je kan voor collision checken voor collision met objecten met een specifieke tag. Dit is handig voor de vloer en enemies.
```c#
private void OnCollisionEnter(Collision collision)
{
	if (collision.gameObject.CompareTag("Ground"))
	{
		isOnGround = true;
	}
	if (collision.gameObject.CompareTag("Enemy"))
	{
		gameOver = true;
		destroy(self);
	}
}
```

Ook kan je .Find gebruiken om een gameObject te vinden. Dit is handig om specifieke objecten aan te spreken
```c#
private GameObject player;

private void Start()
{
	player = GameObject.Find("player");
}
```

Meer is eigenlijk niet heel erg van belang, je kan naar mij toekomen voor meer specifieke vragen.