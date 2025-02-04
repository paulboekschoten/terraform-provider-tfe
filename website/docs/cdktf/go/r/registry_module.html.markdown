---
layout: "tfe"
page_title: "Terraform Enterprise: tfe_registry_module"
description: |-
  Manages registry modules
---


<!-- Please do not edit this file, it is generated. -->
# tfe_registry_module

HCP Terraform's private module registry helps you share Terraform modules across your organization.

## Example Usage

Basic usage with VCS:

```go
import constructs "github.com/aws/constructs-go/constructs"
import "github.com/hashicorp/terraform-cdk-go/cdktf"
/*Provider bindings are generated by running cdktf get.
See https://cdk.tf/provider-generation for more details.*/
import "github.com/aws-samples/dummy/gen/providers/tfe/organization"
import "github.com/aws-samples/dummy/gen/providers/tfe/oauthClient"
import "github.com/aws-samples/dummy/gen/providers/tfe/registryModule"
type myConvertedCode struct {
	terraformStack
}

func newMyConvertedCode(scope construct, name *string) *myConvertedCode {
	this := &myConvertedCode{}
	cdktf.NewTerraformStack_Override(this, scope, name)
	tfeOrganizationTestOrganization := organization.NewOrganization(this, jsii.String("test-organization"), &organizationConfig{
		email: jsii.String("admin@company.com"),
		name: jsii.String("my-org-name"),
	})
	tfeOauthClientTestOauthClient := oauthClient.NewOauthClient(this, jsii.String("test-oauth-client"), &oauthClientConfig{
		apiUrl: jsii.String("https://api.github.com"),
		httpUrl: jsii.String("https://github.com"),
		oauthToken: jsii.String("my-vcs-provider-token"),
		organization: cdktf.Token_AsString(tfeOrganizationTestOrganization.name),
		serviceProvider: jsii.String("github"),
	})
	registryModule.NewRegistryModule(this, jsii.String("test-registry-module"), &registryModuleConfig{
		vcsRepo: &registryModuleVcsRepo{
			displayIdentifier: jsii.String("my-org-name/terraform-provider-name"),
			identifier: jsii.String("my-org-name/terraform-provider-name"),
			oauthTokenId: cdktf.Token_*AsString(tfeOauthClientTestOauthClient.oauthTokenId),
		},
	})
	return this
}
```

Create private registry module with tests enabled:

```go
import constructs "github.com/aws/constructs-go/constructs"
import "github.com/hashicorp/terraform-cdk-go/cdktf"
/*Provider bindings are generated by running cdktf get.
See https://cdk.tf/provider-generation for more details.*/
import "github.com/aws-samples/dummy/gen/providers/tfe/organization"
import "github.com/aws-samples/dummy/gen/providers/tfe/oauthClient"
import "github.com/aws-samples/dummy/gen/providers/tfe/registryModule"
type myConvertedCode struct {
	terraformStack
}

func newMyConvertedCode(scope construct, name *string) *myConvertedCode {
	this := &myConvertedCode{}
	cdktf.NewTerraformStack_Override(this, scope, name)
	tfeOrganizationTestOrganization := organization.NewOrganization(this, jsii.String("test-organization"), &organizationConfig{
		email: jsii.String("admin@company.com"),
		name: jsii.String("my-org-name"),
	})
	tfeOauthClientTestOauthClient := oauthClient.NewOauthClient(this, jsii.String("test-oauth-client"), &oauthClientConfig{
		apiUrl: jsii.String("https://api.github.com"),
		httpUrl: jsii.String("https://github.com"),
		oauthToken: jsii.String("my-vcs-provider-token"),
		organization: cdktf.Token_AsString(tfeOrganizationTestOrganization.name),
		serviceProvider: jsii.String("github"),
	})
	registryModule.NewRegistryModule(this, jsii.String("test-registry-module"), &registryModuleConfig{
		testConfig: []interface{}{
			&registryModuleTestConfig{
				testsEnabled: jsii.Boolean(true),
			},
		},
		vcsRepo: &registryModuleVcsRepo{
			branch: jsii.String("main"),
			displayIdentifier: jsii.String("my-org-name/terraform-provider-name"),
			identifier: jsii.String("my-org-name/terraform-provider-name"),
			oauthTokenId: cdktf.Token_*AsString(tfeOauthClientTestOauthClient.oauthTokenId),
		},
	})
	return this
}
```

Create private registry module with GitHub App:

```go
import constructs "github.com/aws/constructs-go/constructs"
import "github.com/hashicorp/terraform-cdk-go/cdktf"
/*Provider bindings are generated by running cdktf get.
See https://cdk.tf/provider-generation for more details.*/
import "github.com/aws-samples/dummy/gen/providers/tfe/organization"
import "github.com/aws-samples/dummy/gen/providers/tfe/dataTfeGithubAppInstallation"
import "github.com/aws-samples/dummy/gen/providers/tfe/registryModule"
type myConvertedCode struct {
	terraformStack
}

func newMyConvertedCode(scope construct, name *string) *myConvertedCode {
	this := &myConvertedCode{}
	cdktf.NewTerraformStack_Override(this, scope, name)
	tfeOrganizationTestOrganization := organization.NewOrganization(this, jsii.String("test-organization"), &organizationConfig{
		email: jsii.String("admin@company.com"),
		name: jsii.String("my-org-name"),
	})
	dataTfeGithubAppInstallationGhaInstallation :=
	dataTfeGithubAppInstallation.NewDataTfeGithubAppInstallation(this, jsii.String("gha_installation"), &dataTfeGithubAppInstallationConfig{
		name: jsii.String("YOUR_GH_NAME"),
	})
	registryModule.NewRegistryModule(this, jsii.String("petstore"), &registryModuleConfig{
		organization: cdktf.Token_AsString(tfeOrganizationTestOrganization.name),
		vcsRepo: &registryModuleVcsRepo{
			displayIdentifier: jsii.String("GH_NAME/REPO_NAME"),
			githubAppInstallationId: cdktf.Token_*AsString(dataTfeGithubAppInstallationGhaInstallation.id),
			identifier: jsii.String("GH_NAME/REPO_NAME"),
		},
	})
	return this
}
```

Create private registry module without VCS:

```go
import constructs "github.com/aws/constructs-go/constructs"
import "github.com/hashicorp/terraform-cdk-go/cdktf"
/*Provider bindings are generated by running cdktf get.
See https://cdk.tf/provider-generation for more details.*/
import "github.com/aws-samples/dummy/gen/providers/tfe/organization"
import "github.com/aws-samples/dummy/gen/providers/tfe/registryModule"
type myConvertedCode struct {
	terraformStack
}

func newMyConvertedCode(scope construct, name *string) *myConvertedCode {
	this := &myConvertedCode{}
	cdktf.NewTerraformStack_Override(this, scope, name)
	tfeOrganizationTestOrganization := organization.NewOrganization(this, jsii.String("test-organization"), &organizationConfig{
		email: jsii.String("admin@company.com"),
		name: jsii.String("my-org-name"),
	})
	registryModule.NewRegistryModule(this, jsii.String("test-private-registry-module"), &registryModuleConfig{
		moduleProvider: jsii.String("my_provider"),
		name: jsii.String("another_test_module"),
		organization: cdktf.Token_AsString(tfeOrganizationTestOrganization.name),
		registryName: jsii.String("private"),
	})
	return this
}
```

Create public registry module:

```go
import constructs "github.com/aws/constructs-go/constructs"
import "github.com/hashicorp/terraform-cdk-go/cdktf"
/*Provider bindings are generated by running cdktf get.
See https://cdk.tf/provider-generation for more details.*/
import "github.com/aws-samples/dummy/gen/providers/tfe/organization"
import "github.com/aws-samples/dummy/gen/providers/tfe/registryModule"
type myConvertedCode struct {
	terraformStack
}

func newMyConvertedCode(scope construct, name *string) *myConvertedCode {
	this := &myConvertedCode{}
	cdktf.NewTerraformStack_Override(this, scope, name)
	tfeOrganizationTestOrganization := organization.NewOrganization(this, jsii.String("test-organization"), &organizationConfig{
		email: jsii.String("admin@company.com"),
		name: jsii.String("my-org-name"),
	})
	registryModule.NewRegistryModule(this, jsii.String("test-public-registry-module"), &registryModuleConfig{
		moduleProvider: jsii.String("aws"),
		name: jsii.String("vpc"),
		namespace: jsii.String("terraform-aws-modules"),
		organization: cdktf.Token_AsString(tfeOrganizationTestOrganization.name),
		registryName: jsii.String("public"),
	})
	return this
}
```

Create no-code provisioning registry module:

```go
import constructs "github.com/aws/constructs-go/constructs"
import "github.com/hashicorp/terraform-cdk-go/cdktf"
/*Provider bindings are generated by running cdktf get.
See https://cdk.tf/provider-generation for more details.*/
import "github.com/aws-samples/dummy/gen/providers/tfe/organization"
import "github.com/aws-samples/dummy/gen/providers/tfe/registryModule"
import "github.com/aws-samples/dummy/gen/providers/tfe/noCodeModule"
type myConvertedCode struct {
	terraformStack
}

func newMyConvertedCode(scope construct, name *string) *myConvertedCode {
	this := &myConvertedCode{}
	cdktf.NewTerraformStack_Override(this, scope, name)
	tfeOrganizationTestOrganization := organization.NewOrganization(this, jsii.String("test-organization"), &organizationConfig{
		email: jsii.String("admin@company.com"),
		name: jsii.String("my-org-name"),
	})
	tfeRegistryModuleTestNoCodeProvisioningRegistryModule :=
	registryModule.NewRegistryModule(this, jsii.String("test-no-code-provisioning-registry-module"), &registryModuleConfig{
		moduleProvider: jsii.String("aws"),
		name: jsii.String("vpc"),
		namespace: jsii.String("terraform-aws-modules"),
		organization: cdktf.Token_AsString(tfeOrganizationTestOrganization.name),
		registryName: jsii.String("public"),
	})
	noCodeModule.NewNoCodeModule(this, jsii.String("foobar"), &noCodeModuleConfig{
		organization: cdktf.Token_*AsString(tfeOrganizationTestOrganization.id),
		registryModule: cdktf.Token_*AsString(tfeRegistryModuleTestNoCodeProvisioningRegistryModule.id),
	})
	return this
}
```

## Argument Reference

The following arguments are supported:

* `VcsRepo` - (Optional) Settings for the registry module's VCS repository. Forces a
  new resource if changed. One of `VcsRepo` or `ModuleProvider` is required.
* `ModuleProvider` - (Optional) Specifies the Terraform provider that this module is used for. For example, "aws"
* `Name` - (Optional) The name of registry module. It must be set if `ModuleProvider` is used.
* `Organization` - (Optional) The name of the organization associated with the registry module. It must be set if `ModuleProvider` is used, or if `VcsRepo` is used via a GitHub App.
* `Namespace` - (Optional) The namespace of a public registry module. It can be used if `ModuleProvider` is set and `RegistryName` is public.
* `RegistryName` - (Optional) Whether the registry module is private or public. It can be used if `ModuleProvider` is set.

The `TestConfig` block supports
* `TestsEnabled` - (Optional) Specifies whether tests run for the registry module. Tests are only supported for branch-based publishing.

The `VcsRepo` block supports:

* `DisplayIdentifier` - (Required) The display identifier for your VCS repository.
  For most VCS providers outside of BitBucket Cloud and Azure DevOps, this will match the `Identifier`
  string.
* `Identifier` - (Required) A reference to your VCS repository in the format
  `<organization>/<repository>` where `<organization>` and `<repository>` refer to the organization (or project key, for Bitbucket Data Center)
  and repository in your VCS provider. The format for Azure DevOps is `<ado organization>/<ado project>/_git/<ado repository>`.
* `OauthTokenId` - (Optional) Token ID of the VCS Connection (OAuth Connection Token) to use. This conflicts with `GithubAppInstallationId` and can only be used if `GithubAppInstallationId` is not used.
* `GithubAppInstallationId` - (Optional) The installation id of the Github App. This conflicts with `OauthTokenId` and can only be used if `OauthTokenId` is not used.
* `Branch` - (Optional) The git branch used for publishing when using branch-based publishing for the registry module. When a `Branch` is set, `Tags` will be returned as `False`.
* `Tags` - (Optional) Specifies whether tag based publishing is enabled for the registry module. When `Tags` is set to `True`, the `Branch` must be set to an empty value.

## Attributes Reference

* `Id` - The ID of the registry module.
* `ModuleProvider` - The Terraform provider that this module is used for.
* `Name` - The name of registry module.
* `Organization` - The name of the organization associated with the registry module.
* `Namespace` - The namespace of the module. For private modules this is the name of the organization that owns the module.
* `PublishingMechanism` - The publishing mechanism used when releasing new versions of the module.
* `RegistryName` - The registry name of the registry module depicting whether the registry module is private or public.
* `NoCode` - **Deprecated** The property that will enable or disable a module as no-code provisioning ready.
Use the tfe_no_code_module resource instead.

## Import

Registry modules can be imported; use `<ORGANIZATION>/<REGISTRY_NAME>/<NAMESPACE>/<REGISTRY MODULE NAME>/<REGISTRY MODULE PROVIDER>/<REGISTRY MODULE ID>` as the import ID. For example:

```shell
terraform import tfe_registry_module.test my-org-name/public/namespace/name/provider/mod-qV9JnKRkmtMa4zcA
```

**Deprecated** use `<ORGANIZATION NAME>/<REGISTRY MODULE NAME>/<REGISTRY MODULE PROVIDER>/<REGISTRY MODULE ID>` as the import ID. For example:

```shell
terraform import tfe_registry_module.test my-org-name/name/provider/mod-qV9JnKRkmtMa4zcA
```

<!-- cache-key: cdktf-0.17.0-pre.15 input-456a79854887a1ea146b73701b97c25121ac10198e434b748c3268fc7de9d53f -->