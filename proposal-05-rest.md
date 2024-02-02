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
Cartesify.axios.post("http://localhost:8383/hit", { foo: "bar" })
```
