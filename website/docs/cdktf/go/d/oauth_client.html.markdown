---
layout: "tfe"
page_title: "Terraform Enterprise: tfe_oauth_client"
description: |-
  Get information on an OAuth client.
---

# Data Source: tfe_oauth_client

Use this data source to get information about an OAuth client.

## Example Usage

### Finding an OAuth client by its ID

```go
import constructs "github.com/aws/constructs-go/constructs"
import cdktf "github.com/hashicorp/terraform-cdk-go/cdktf"
/*Provider bindings are generated by running cdktf get.
See https://cdk.tf/provider-generation for more details.*/
import "github.com/aws-samples/dummy/gen/providers/tfe/dataTfeOauthClient"
type myConvertedCode struct {
	terraformStack
}

func newMyConvertedCode(scope construct, name *string) *myConvertedCode {
	this := &myConvertedCode{}
	cdktf.NewTerraformStack_Override(this, scope, name)
	dataTfeOauthClient.NewDataTfeOauthClient(this, jsii.String("client"), &dataTfeOauthClientConfig{
		oauthClientId: jsii.String("oc-XXXXXXX"),
	})
	return this
}
```

### Finding an OAuth client by its name

```go
import constructs "github.com/aws/constructs-go/constructs"
import cdktf "github.com/hashicorp/terraform-cdk-go/cdktf"
/*Provider bindings are generated by running cdktf get.
See https://cdk.tf/provider-generation for more details.*/
import "github.com/aws-samples/dummy/gen/providers/tfe/dataTfeOauthClient"
type myConvertedCode struct {
	terraformStack
}

func newMyConvertedCode(scope construct, name *string) *myConvertedCode {
	this := &myConvertedCode{}
	cdktf.NewTerraformStack_Override(this, scope, name)
	dataTfeOauthClient.NewDataTfeOauthClient(this, jsii.String("client"), &dataTfeOauthClientConfig{
		name: jsii.String("my-oauth-client"),
		organization: jsii.String("my-org"),
	})
	return this
}
```

### Finding an OAuth client by its service provider

```go
import constructs "github.com/aws/constructs-go/constructs"
import cdktf "github.com/hashicorp/terraform-cdk-go/cdktf"
/*Provider bindings are generated by running cdktf get.
See https://cdk.tf/provider-generation for more details.*/
import "github.com/aws-samples/dummy/gen/providers/tfe/dataTfeOauthClient"
type myConvertedCode struct {
	terraformStack
}

func newMyConvertedCode(scope construct, name *string) *myConvertedCode {
	this := &myConvertedCode{}
	cdktf.NewTerraformStack_Override(this, scope, name)
	dataTfeOauthClient.NewDataTfeOauthClient(this, jsii.String("client"), &dataTfeOauthClientConfig{
		organization: jsii.String("my-org"),
		serviceProvider: jsii.String("github"),
	})
	return this
}
```

## Argument Reference

The following arguments are supported. At least one of `Name`, `OauthClientId`,
or `ServiceProvider` must be set. `Name` and `ServiceProvider` may be used
together. If either `Name` or `ServiceProvider` is set, `Organization` must also
be set.

* `Name` - (Optional) Name of the OAuth client.
* `OauthClientId` - (Optional) ID of the OAuth client.
* `Organization` - (Optional) The name of the organization in which to search.
* `ServiceProvider` - (Optional) The API identifier of the OAuth service provider. If set,
  must be one of: `AdoServer`, `AdoServices`, `BitbucketDataCenter`, `BitbucketHosted`, `BitbucketServer`(deprecated),
  `Github`, `GithubEnterprise`, `GitlabHosted`, `GitlabCommunityEdition`, or
  `GitlabEnterpriseEdition`.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `Id` - The OAuth client ID. This will match `OauthClientId`.
* `ApiUrl` - The client's API URL.
* `CallbackUrl` - OAuth callback URL to provide to the OAuth service provider.
* `CreatedAt` - The date and time this OAuth client was created in RFC3339 format.
* `HttpUrl` - The client's HTTP URL.
* `OauthTokenId` - The ID of the OAuth token associated with the OAuth client.
* `Name` - The name of the OAuth client (may be `Null`).
* `Organization` - The organization in which the OAuth client is registered.
* `ServiceProvider` - The API identifier of the OAuth service provider.
* `ServiceProviderDisplayName` - The display name of the OAuth service provider.

<!-- cache-key: cdktf-0.17.0-pre.15 input-59b4bcbbb310e7ee913a245f3c751829442542dbcf1bbb4c87ac286043b69348 -->
