# Installation Guide

* goal
  * install an Atlantis **production-ready** instance | your infrastructure

* steps
  1. [Requirements](requirements.md)
  1. [Create Git Host Access Credentials](access-credentials.md)
  1. [Creating a Webhook Secret](webhook-secrets.md)
  1. [deploy Atlantias | your infrastructure](deployment.md)
  1. TODO: Configure **Webhooks** on your Git host so Atlantis can respond to your pull requests
      * See [Configuring Webhooks](configuring-webhooks.md)
  1. Configure **provider credentials** so Atlantis can actually run Terraform commands
      * See [Provider Credentials](provider-credentials.md)

:::tip
If you want to test out Atlantis first, check out [Test Drive](../guide/test-drive.md)
and [Testing Locally](../guide/testing-locally.md).
:::
