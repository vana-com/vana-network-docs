# TEE Validators

The Vana network utilizes independent Trusted Execution Environment (TEE) validators to perform data validation requests for DLPs, simplifying their architecture by eliminating the need for DLPs to operate their own validator nodes. Each TEE validator node is a sealed, encrypted virtual machine running on an independently operated server with a bare metal install of [Intel SGX](https://www.intel.com/content/www/us/en/products/docs/accelerator-engines/software-guard-extensions.html), an advanced hardware-level isolation technology.&#x20;

This setup ensures that neither the node operators nor any other parties can access the interior of the processor or the data being processed. The TEE environment guarantees that deployed programs within it are immutable and private, maintaining operational integrity and preventing unauthorized changes while processing user data.

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>A DLP that relies on TEE validators</p></figcaption></figure>

## **Responsibilities**

* Verify user data by running Proof-of-Contribution to assess data legitimacy and value.
* Attest to the validity of the data and write the attestation back on-chain.

{% hint style="warning" %}
TEE Validators are a work in progress. Code samples and technical documentation will be added soon.
{% endhint %}

## Data Flow

A detailed data flow diagram of how TEE Validators operate can be [found here](https://mermaid.live/view#pako:eNqlV21v2kgQ\_isrS5USyRAIARJ\_qASlVNVdL6hAPlSR0GIPYMV4fbvrtCTKf7\_Z8fsL6Z0uikJYP\_Oyzzwzu361XOGB5VgK\_o4hdGHm873kx8eQ4c-HDyziUvuuH\_FQs4c544o98JCzuYhDj2tfhAmyDFt9\_tyyuPhkjPEZWwgRsE8i1JK7uolcG9xagWw--rqYL81T83m11ELyPTRR8-8Uau4HwL7D3ldant6Jt1pQYjJWGjy2wCenJmj2J6HMx3lPs8l9y-KUDLnmbBqfzK5ybv8SGph4BonM2kiQw-4jQykPiKcl6DhiPPTYA0h\_57slvtEaIZ2PH\_Gvw\_pd9gVCkBz9PcEp4r5kfsgUuLEEhmUN-DO0GV53kSEsvNKMa40fFILtpDiyA5feTy4bdibPQZct4-3Rr5jlwId5hrvpJrmfKu7FbtdxD9xvsxh2GY8iiaysAC40wMTzJCh1mfFWkLa2sdJOUud1FAjuEVlpyUsprdH5usrSDo02SJVt2JGnSNNKATcKI3pSxykKBVLgDKaTuB4YHnUswwK4wfbgm1gGhVNKFynhnmeSvmhiLxMwAlPHw9wxZex7TRqwLCgehy2kEDvkNhGov42J63THORc80EkTGnSylKVH\_CNJe9DI\_RzpvywA-DBN6TpPCauz2QG0eEE-ZKKrcjIU8yLdiM1e2TMPYnAyP-ytFq8Q0UQpfx8yaaZOR4otijufMtXsCsIOWkfO1RU67\_S7rjjW0jTyH6EiPq8ayKuGqEsqGueSNjSWZW3Ep\_gOsvlRCXXbZYv7ZRarCOWW-OlEhiDFiCJmKCoUkgm2TFHRx3claUfVylaFQhI0Sw5zRRxgxwRKYK2IMbJkWrAYp6\_Nfh6EkapqRCSd9LoMx4p\_RJ1MQg-7tFZdU1RyaCd-N\_gLv3AimZ22F7rfz7nNkfXtJHDaRv-aWulc3KZ4k1lJvRoAV1AVMAS48uOPts6oDQ8ERU0Q5dSa0stTJSMKVDlv2mImW0R3sT4I6b9A4W-12ETxNvDdygQ7I5JFKTXsbBo8qacSLJ04Zo68N8vagtViGRdJx-LUpqnFjMYh1KpVlIv\_q8l8g8NWOURV7kOv7SDBc90pDve0HWuDu70WaPTvimH8UJjrYjaa\_qkVAyFZwMG5gqXFIm83\_7FaaTeqcjRyNORdYsADMlGtts90EQHFfAQcuDo03WzzHk6nmRmLLg\_cODC9IwHvFF7ZbE1z-KtSMVACWjxBqMylKcPW6zWb2mhEV6pFLPEmodIWnk1NGpN7KlZ2sUHtRCmKGWZS6OS-k4GxIl-M45DjBZg9Y5wqZkq1mCTXksJZWsXiXJ2aMqwo\_UKfSU5UKmQ4MzbJl0RKNhstNlt0UWrLWn0ogC4FoFGy4Ce21HwbgCv8sDXy9lxkldttIn46YpeeiY4eZuZaZXoDOUiwhltKhx1E4IFUpSarEYglXuJ6Ji8z2fPZQYmS5Me\_k\_yUTtLf3LXIX3KDw4NxDto91C5wOE38cP--AxPLnHKzJGPScZxqyLKtI8gj9z18dXo1Ro-WPsARHi0H\_\_W4fHq0HsM3xOHMEMtT6FqOljHYFt5h9gfL2eGQw29xhO6yl64MAp6P7zbfkhczej-zLXyX-CFEDsGvlvNq\_bKc4c2wO7wdj-5ue73B-K4\_sq0Trg66N6PeaNi\_HffGo95w8GZbL2Tf794Nrnv9Ia6OB\_1Bfzx8-we14Gb5).
