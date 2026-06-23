# IndustryComplete: Installation Walkthrough

Welcome to IndustryComplete by ProvenWorks. A streamlined way to start classifying your Accounts and Leads in Salesforce with industry codes from SIC, ISIC and NAICS industry standards. Follow the steps below to configure the solution and up your industry game.

---

## Industry Code Management

### Installing Industry Codes

#### What are Industry Codes?

Industry Codes belong to standards that have been developed to assist with classifying industries into categories. There are three main Industry Standards:

- `Standard Industrial Classification (SIC)`
- `International Standard Industrial Classification (ISIC)`
- `North American Industry Classification System (NAICS)`

#### What Industry Code Standards are available in IndustryComplete?

IndustryComplete supports the following codes out of the box:

- `ISICr40`
- `NAICS07`
- `NAICS12`
- `NAICS17`
- `NAICS22`
- `USSIC87`

You have the ability to customize existing industry code standards or create your own in your organization. See [Customize Industry Codes](#customize-industry-codes) for more information.

#### How to Install Industry Codes

1. Go to **App Launcher | IndustryComplete Administration**.
2. Ensure that you're on the **Installation & Settings** page.
3. Under the **Install Industries** heading, select the industry codes which you would like to install.
4. Select **Install Industries**.
5. Wait for the process to finish.

#### Customize Industry Codes

During installation, the Industry Codes will be inserted into the `pw_ic__IndustryCode__c` object that is created with the IndustryComplete managed package. You have the ability to customize these records to meet your organizational requirements as you would any other record in your Salesforce environment.

A common change is to remove the standard name from the industry code name field. This can be beneficial for integrations that don't expect an industry standard prefix to the codes.

**Example:** `NAICS17-531210` will be installed with the NAICS17 data set. You can remove the `NAICS17-` from the record name leaving just `531210`.

As the Industry Codes object is created in your organization, you can create custom fields on the object to store relevant information on the codes.

---

## Account Setup

### Enabling the Account Trigger

#### Enable the Account Trigger

1. Go to **App Launcher | IndustryComplete Administration**.
2. Ensure that you're on the **Installation & Settings** page.
3. Under the **Settings** heading, select the **Enable IndustryComplete trigger (Account)** checkbox.
4. Select **Save**.

#### What Settings are Available with the Account Trigger?

The package comes with three trigger settings for the Account object:

- Populate Accounts' `Industry` field from their `Industry Code Lookup (IndustryCodeLookup__c)` field
- Populate Accounts' `Industry Code Lookup (IndustryCodeLookup__c)` field from their `SIC` field
- Populate Accounts' `SIC` field from their `Industry Code Lookup (IndustryCodeLookup__c)` field

### Setting up the Industry Lookup Component on the Account Object

#### How to Add the Industry Lookup Component to your Organization

1. Navigate to **Setup | Object Manager | Account | Lightning Record Pages**.
2. If an Account Lightning Record Page already exists, select **Edit**.
3. If you need to create a new Account Lightning Record Page, select **New** and follow the onscreen steps.
4. Drag the **Industries Lookup** component from the components list onto the layout.
5. Select **Save** and **Activate**.

Now your account page(s) will be set up with the IndustryComplete Industries Lookup component ready for use.

---

## Lead Setup

### Enabling the Lead Trigger

#### Enable the Lead Trigger

1. Go to **App Launcher | IndustryComplete Administration**.
2. Ensure that you're on the **Installation & Settings** page.
3. Under the **Settings** heading, select the **Enable IndustryComplete trigger (Lead)** checkbox.
4. Select **Save**.

#### What Settings are Available with the Lead Trigger?

The package comes with one trigger setting for the Lead object:

- Populate Leads' `Industry` field from their `Industry Code Lookup (IndustryCodeLookup__c)` field

### Setting up the Industry Lookup Component on the Lead Object

#### How to Add the Industry Lookup Component to your Organization

1. Navigate to **Setup | Object Manager | Lead | Lightning Record Pages**.
2. If a Lead Lightning Record Page already exists, select **Edit**.
3. If you need to create a new Lead Lightning Record Page, select **New** and follow the onscreen steps.
4. Drag the **Industries Lookup** component from the components list onto the layout.
5. Select **Save** and **Activate**.

Now your lead page(s) will be set up with the IndustryComplete Industries Lookup component ready for use.

### Map Industry Code Lookup for Lead Conversion

#### Why Do I Need to Make Changes to the Lead Conversion Process?

When using IndustryComplete, the component will populate a custom lookup field (`pw_ic__IndustryCode__c`) on the Lead records. When a Lead is converted to an Account, it is preferable to retain this information on the Account record. This can be achieved using the **Map Lead Fields** functionality in Salesforce Setup.

#### Map Lead Fields

1. Go to **Salesforce Setup | Object Manager | Lead | Fields & Relationships**.
2. Select **Map Lead Fields**.
3. Ensure the **Account** tab is selected.
4. Next to **Industry Code Lookup**, use the picklist in the **Account Fields** column and select **Industry Code Lookup**.
5. Select **Save**.

Now when converting a Lead, the Industry Code Lookup will be pushed to the Account.
