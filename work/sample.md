


## Statement and Transparet Statement


### Signed Statement
```
Signed_Statement = #6.18(COSE_Sign1)
Receipt = #6.18(COSE_Sign1)

COSE_Sign1 = [
  protected   : bstr .cbor Protected_Header,
  unprotected : Unprotected_Header,
  payload     : bstr / nil,
  signature   : bstr
]

Protected_Header = {
  &(CWT_Claims: 15) => CWT_Claims
  ? &(alg: 1) => int
  ? &(content_type: 3) => tstr / uint
  ? &(kid: 4) => bstr
  ? &(x5t: 34) => COSE_CertHash
  * int => any
}

CWT_Claims = {
  &(iss: 1) => tstr
  &(sub: 2) => tstr  ## Can put the statement id
  * int => any
}

Unprotected_Header = {
  ? &(x5chain: 33) => COSE_X509
  ? &(receipts: TBD_0)  => [+ Receipt]
  * int => any
}
```