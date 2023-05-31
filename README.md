# go-btns

> btns record definitions

This package contains all of the components necessary to create, understand, and validate BTNS records. It does *not* publish or resolve those records. [`go-btfs`](https://github.com/bittorrent/go-btfs) uses this package internally to manipulate records.

## Usage

To create a new BTNS record:

```go
import (
    "time"

    btns "github.com/bittorrent/go-btns"
    crypto "github.com/libp2p/go-libp2p-crypto"
)

// Generate a private key to sign the BTNS record with. Most of the time, 
// however, you'll want to retrieve an already-existing key from BTFS using the
// go-btfs/core/coreapi CoreAPI.KeyAPI() interface.
privateKey, publicKey, err := crypto.GenerateKeyPair(crypto.RSA, 2048)
if err != nil {
    panic(err)
}

// Create an BTNS record that expires in one hour and points to the BTFS address
// /btfs/Qme1knMqwt1hKZbc1BmQFmnm9f36nyQGwXxPGVpVJ9rMK5
btnsRecord, err := btns.Create(privateKey, []byte("/btfs/Qme1knMqwt1hKZbc1BmQFmnm9f36nyQGwXxPGVpVJ9rMK5"), 0, time.Now().Add(1*time.Hour))
if err != nil {
    panic(err)
}
```

Once you have the record, you’ll need to use BTFS to *publish* it.

There are several other major operations you can do with `go-btns`. Check out the [API docs](https://pkg.go.dev/github.com/bittorrent/go-btns) or look at the tests in this repo for examples.

## Documentation

https://pkg.go.dev/github.com/bittorrent/go-btns

## Contribute

Feel free to join in. All welcome. Open an [issue](https://github.com/bittorrent/go-btns/issues)!

## License

Copyright (c) Bittorrent. 
