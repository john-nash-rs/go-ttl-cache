A very detailed post can be found at https://nulpointerexception.com/2023/03/19/design-a-ttl-based-in-memory-cache-in-golang/
# Initialisation
## Options
1. **defaultExpiryDuration** - If the key value pair is stored without ttl. This defaultExpirationTime becomes the default ttl. If the value of defaultExpiryDuration is specified as 0, it is treated as infinity.
2. **expiryDuration** - if the key value pair is set with value of 0, defaultExpiryDuration will be set as ttl. -1 as expiryDuration would mean that keyvalue pair would never be expired. Other than these two, the given value will be used as ttl.
## Usage
```
func main() {
	fmt.Println("Hello World")
	cache := New(10*time.Hour, 20*time.Minute)
	fmt.Println(cache.defaultExpiryDuration)
	fmt.Println(cache.kvstore)
	cache.Set("foo", "bar", 2*time.Minute)
	fmt.Println(cache.kvstore)
	value, found := cache.Get("foo")
	if found {
		fmt.Println("Value is ", value)
	}
}
```
