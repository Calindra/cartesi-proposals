# Cartesify HLF

Bruno and I are focused on growing Cartesi's adoption, especially among web2 developers. Our proposal introduces a REST abstraction layer to the current technology stack, aiming to simplify onboarding. By taking advantage of the familiarity developers have with RESTful architectures, we aim to facilitate the transition from web2 to web3 with minimal effort. This approach aligns with our goal of creating a more developer-friendly ecosystem and expanding Cartesi's reach within the broader community.

## Statistics

The latest Stack Overflow survey shows that the majority of developers are web developers.
https://survey.stackoverflow.co/2023/#section-developer-roles-developer-type

![Stackoverflow Survey 2023](https://github.com/Calindra/cartesi-proposals/blob/main/images/stackoverflow-survey-2023.png?raw=true)

## Some Advantages

1. **Low Learning Curve:**
   - Web2 developers are already familiar with REST APIs, making it easier for them to transition into Cartesi Rollups without a steep learning curve.
   - Leveraging existing knowledge helps developers become productive more quickly.

2. **Widely Adopted:**
   - REST is a widely adopted in the development community, ensuring compatibility with a broad range of programming languages and frameworks.
   - This increases the chances of widespread adoption and support within the developer community.

3. **Adapting Existing Systems:**
   - Many web2 applications are built on RESTful architectures, and integrating Cartesi Rollups through REST would allow for migration with existing systems with low effort.
   - This enables developers to incorporate Cartesi technology into their current projects viable.

4. **Future evolution:**
   - The basic HTTP calls will allow this HLF to start with RESTful APIs and later evolve to more complex communication protocols like GraphQL or gRPC.

5. **Community Adoption:**
   - By providing a REST API for Cartesi Rollups, you can attract a larger audience, particularly developers who may not be familiar with blockchain or specialized technologies.

6. **Documentation and Tooling:**
   - RESTful APIs come with established standards for documentation (e.g., OpenAPI) and tooling, making it easier for developers to understand, use, and integrate Cartesi Rollups.

## Example

Given this minimal backend code:
```js
const express = require("express")

const app = express();
const port = 8383;
app.use(express.json());

app.post('/hit', (req, res) => {
    res.send({ amount: req.body.amount });
});

app.listen(port, () => {
    console.log(`[server]: Server is running at http://localhost:${port}`);
});
```

The frontend code to make an HTTP POST request to the backend using Cartesify will be:
```ts
const handleHit = async () => {
    const res = await Cartesify.axios.post("/hit", { amount: 1234 });
    console.log(res.data);
}
```
When triggered, the code above will print `{"amount": 1234}` in the console.

## Tech details

![Cartesi Tech Diagram](https://github.com/Calindra/cartesi-proposals/blob/main/images/cartesify-diagram.png?raw=true)

All the REST verbs that make changes to the state (POST, PUT, PATCH, DELETE) will be signed by the private key, possibly using a wallet like MetaMask, and will be implemented using the `advance` command. The GET operation will be implemented using the `inspect` command.

As a web2 developer, we will achieve battle-proof authentication by adding the `msg_sender` to the request headers.

```js
// express code
app.post('/hit', (req, res) => {
    const msgSender = req.get('x-msg_sender');
    res.send({ amount: req.body.amount });
});
```

Additionally, web2 developers will benefit from an atomic operation. If the endpoint returns an error, such as a 4xx or 5xx status code, we will send a `reject` that performs a rollback operation, thanks to the Cartesi technology as pointed out by @gabrielbarros.

### Deposit

We will set up a protected webhook by convention, pointing to /webhooks/deposits, which can be configurable.

```json
{
    "success": true,
    "erc20": "0x4ed7c70F96B99c776995fB64377f0d4aB3B0e1C1",
    "depositor": "0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266",
    "amount": "100",
}
```
