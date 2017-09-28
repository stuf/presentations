## The Anatomy of Observables

v-v-v

|          | Single     | Multiple     |
|----------|------------|--------------|
| **Pull** | `Function` | `Iterator`   |
| **Push** | `Promise`  | `Observable` |

note:

- pull and push are concepts brought up on the thought of how data is propagated to some section (described in next slide)
- regular data is pull, while reactive/future data is push

v-v-v

|          | Producer | Consumer |
|----------|----------|----------|
| **Pull** | **Passive**<br><small>produces data when requested</small> | **Active**<br><small>decides when data is requested</small> |
| **Push** | **Active**<br><small>produces data at its own pace</small> | **Passive**<br><small>reacts to received data</small>       |

note:

- the contrast between the two is simply in which who is passive and who is active
- `pull` data requires us to manually "pull" the data _when_ we need it
- `push` allows us to passively _observe_ data, without needing to think _when_

v-v-v


