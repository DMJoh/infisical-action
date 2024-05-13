## Infisical integration for GitHub Actions

**This service & API token will be deprecated soon See [here](https://infisical.com/blog/deprecating-api-keys)**   
This action will fetch secrets from infisical instance to Github actions workflow.  

**_NOTE: Applies only for self-hosted Infisical instances (others may work)._**

#### Input variables

|Input parameter|Descripton|Default value| Required |   
|------|-----|-----|-----|
|infisical_url|The url of the infisical instance eg: `https://app.infisical-host.com`|None|yes|
|output_file|File path where the environment variables will be written|.env|yes|
|service_token| Service token<sup>*</sup> created from infisical | None | yes |

<sup>*</sup> To create a service token, Go to Project > Auth Secrets > Service Tokens  

#### Usage  

- Add `INFISICAL_SERVICE_TOKEN`, `INFISICAL_URL` and `OUTPUT_FILE` to repository/environment secrets or variables.

```yaml
  build:
    runs-on: ubuntu-latest
    steps:
      - run: sudo apt update; sudo apt install curl jq -y
      - name: Get Infisical Secrets
        uses: DMJoh/infisical-action@v0.0.4
        with:
          service_token: ${{ secrets.INFISICAL_SERVICE_TOKEN }}
          output_file: ${{ vars.OUTPUT_FILE }}
          infisical_url: ${{ secrets.INFISICAL_URL }}
```
