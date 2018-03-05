# Mga Bayad sa Sistema

## Mga bayad sa transaksyon

Kasalukuyang walang bayad ang mga transaksyon. Ang gumagmit, gayunpaman, ay maaring pumiling bumayad para sa prayoridad.

## Mga Bayad sa Smart na Kontrata

Ang istraktura ng bayad para sa mga Smart na Kontrata ay makikita sa mga talahanayan sa ibaba.

Ang inisyal na 10 GAS sa panahon ng bawat isang eksekusyon ng bawat isang smart na kontrata palaging libre, kabilang ang pag-deploy at pag-invoke. Yan ay, kung ang bayad ay naghahalaga ng 10 GAS o mas mababa pa ay hindi kinakailangang bumayad sa serbisyo.

Ang bayad sa ibaba ay ang pinakamaliit na bayad. Ang gumagamit ay maaring pumili na bumayad ng ekstra para sa prayoridad.

Ang lahat ng bayad para sa mga Smart na Kontrata ay kinokonsiderang Service fee na ilalagay sa isang pool para ipamahagi uli sa lahat ng may hawak ng NEO. Ang pamamahagi ay proporsyonal sa dami ng NEO.

### Mga Bayad para sa Mga Pagtawag sa Sistema

| SysCall                               | Fee [Gas] |
| ------------------------------------- | :-------: |
| Runtime.CheckWitness                  |    0.2    |
| Blockchain.GetHeader                  |    0.1    |
| Blockchain.GetBlock                   |    0.2    |
| Blockchain.GetTransaction             |    0.1    |
| Blockchain.GetAccount                 |    0.1    |
| Blockchain.GetValidators              |    0.2    |
| Blockchain.GetAsset                   |    0.1    |
| Blockchain.GetContract                |    0.1    |
| Transaction.GetReferences             |    0.2    |
| Account.SetVotes                      |     1     |
| Validator.Register                    |   1000    |
| Asset.Create (system asset)           |   5000    |
| Asset.Renew (system asset) [per year] |   5000    |
| Contract.Create                       | 100~1000  |
| Contract.Migrate                      | 100~1000  |
| Storage.Get                           |    0.1    |
| Storage.Put [per KB]*                 |     1     |
| Storage.Delete                        |    0.1    |
| (Default)                             |   0.001   |

* Karagdagan sa 1 GAS na minimum

### Bayad para sa mga Instruksyon

| Instruction                          | Fee [Gas] |
| ------------------------------------ | :-------: |
| OpCode.PUSH16 [or less]              |     0     |
| OpCode.NOP                           |     0     |
| OpCode.APPCALL                       |   0.01    |
| OpCode.TAILCALL                      |   0.01    |
| OpCode.SHA1                          |   0.01    |
| OpCode.SHA256                        |   0.01    |
| OpCode.HASH160                       |   0.02    |
| OpCode.HASH256                       |   0.02    |
| OpCode.CHECKSIG                      |    0.1    |
| OpCode.CHECKMULTISIG [per signature] |    0.1    |
| (Default)                            |   0.001   |

