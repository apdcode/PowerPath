### PowerApps Environment

    https://make.powerapps.com/e/c9528a9c-30c1-ead1-9d99-f3413533305d/s/00000001-0000-0000-0001-00000000009b/app/edit/9263d877-6d6b-ed11-9560-000d3a667e91


# Approach 1

1 - Create a model driven app

1.1 -  Create a Model Driven app with `create solution` as per [Create your model-driven app](https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/build-first-model-driven-app)

1.2 -  Display Name = `IDD`

1.3 - Publisher: Selected option 2: `Default publisher for orge246d87`

1.4 => Ny løsning [IDD](https://make.powerapps.com/environments/c9528a9c-30c1-ead1-9d99-f3413533305d/solutions/20cf3a9c-f68c-ed11-81ac-000d3ada4260)

2 - Set up a Sharepoint list

# Approach 2

2.1 Follow the steps on [YT - PowerApps Single Form App to Save Data in SharePoint List](https://www.youtube.com/watch?v=vArQS8y9BRk&ab_channel=KeaPointTechTips)

2.2 Used user `apdcode@xryk4.onmicrosoft.com`

2.3 Added Sharepoint List [Organization Information](https://xryk4-my.sharepoint.com/personal/apdcode_xryk4_onmicrosoft_com/Lists/IDD%20%20Organization%20Information/AllItems.aspx?env=WebViewList&origin=createList)

This list is simply the first table in the original excel file Vendor Due Diligence Template. It seems clear that this list will only serve as a template for how to *`enter`* the data and not *`store`* the data.

2.4 Followed every step of the above link, these are te findings:

2.4.1.1 App Location for editing [IDD1](https://make.powerapps.com/e/c9528a9c-30c1-ead1-9d99-f3413533305d/canvas/?utm_source=office&utm_medium=app_launcher&utm_campaign=office_referrals&action=edit&form-factor=tablet&name=IDD1&app-id=%2Fproviders%2FMicrosoft.PowerApps%2Fapps%2Fd7e9bef0-a82f-4d3c-8657-f5c31cabe3e4)

2.4.1.2 App location for use: [Power Apps](https://make.powerapps.com/environments/c9528a9c-30c1-ead1-9d99-f3413533305d/apps?utm_source=office&utm_medium=app_launcher&utm_campaign=office_referrals#)

2.4.1.3  List location [Sharepoint lists](https://xryk4-my.sharepoint.com/personal/apdcode_xryk4_onmicrosoft_com/Lists/IDD%20%20Organization%20Information/AllItems.aspx?env=WebViewList)

2.4.2 Possible additional steps in [PowerApps: Edit and Submit Form](https://piyushksingh.com/2018/09/20/powerapps-edit-and-submit-form/)

2.4.2 Unable to move from Success Screen back to Screen1|Form1 => Raises error 

=> Possible solution 1: Use `Notify` instead -> [is it possible to show success screen then move to another screeN?](https://powerusers.microsoft.com/t5/Building-Power-Apps/is-it-possible-to-show-success-screen-then-move-to-another/td-p/971999)

=> Possible solution 2: add a timed delay for `SuccesScrenn1` -> [How To Add Delay Or Wait Until In PowerApps](https://www.c-sharpcorner.com/article/how-to-add-delay-or-wait-until-in-powerapps/)

=> Solution! The `OnSuccess` property of `Form1` needed to be set to `ResetForm(Form1); RequestHide()` as explained in [PowerApp forms get stuck on "Getting your data..."
](https://techcommunity.microsoft.com/t5/power-apps-power-automate/powerapp-forms-get-stuck-on-quot-getting-your-data-quot/m-p/229389)

## Key insights:

Use `Notify` as an alternative to an OnSuccess Screen:

    # Form>OnSuccess
    Notify(
        "Operation Successful",
        NotificationType.Success,
        5000
    ); // This is where you new command starts
    Navigate(
        Home,
        ScreenTransition.Fade
    )

# Approach 3

3.1 Follow steps on [YT - PowerApps Bulk Save to SharePoint List Demo](https://www.youtube.com/watch?v=Tp5CxU3VQOs&ab_channel=KeaPointTechTips)

### Resources

[YT: Power Apps Search and Filter Function with SharePoint + Workarounds](https://www.youtube.com/watch?v=lYi24okXDPs&ab_channel=ShaneYoung)


[MS: Power Apps model-driven apps documentation](https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/)