# Building locally

Even if you have set an automated build in GitHub or whatever, it is always good to be able to build content locally so you can be sure that it builds properly, and nothing you have just done breaks the automated build.

The easiest way to do this is from within Oxygen XML Author. To create a build with Oxygen:

1. With the map you want to build open in the DITA Maps Manager, go to **DITA Maps**>**Configure Transformation Scenarios**.
1. If the transformation scenario you want to use is already there, select it and simply click **Apply associated**. If not, follow these steps to set up a new transformation scenario:
    1. Click **New**>**DITA-OT Transformation**, select the transformation type you want from the list, and click **OK**.
    1. In the **New Scenario** dialog that opens, enter a **Name** and set **Storage** to **Global Options**.
    1. Click the **Parameters** tab, and enter any parameters you require. These will vary according to the transformation type you are using.
    1. Click the **Filters** tab, and indicate any ditaval file you want to use in the **Use DITAVAL file** field.
    1. Click the **Output** tab and set a **Temporary files directory** and an **Output directory**. These should both be outside of the GitHub directory that contains the repository folder containing your ditamap.Then click **OK**.
    1. Finally, select your new scenario from the list, and click **Apply associated** to build it.
1. If you set the **Options**>**Preferences**>**DITA**>**Logging**>**Show console output** option to **Always**, you see the build log scroll past in a window at the bottom of Oxygen XML Author.
1. If it builds successfully, you can find the tranformed content in the folder you indicated as the **Output directory**.

## Sharing transformation scenarios {.section}

If you have configured a scenario that works correctly, you can share it with other writers.

1. Go to **DITA Maps**>**Configure Transformation Scenarios**, right-click the scenario you want to share, and select **Export selected scenario(s)**.
1. Give the scenario a **File Name**, select a folder on your system to save it to, and click **Save**.
1. Click **OK**, and then **Close**.
1. You can then share the resultant *.scenarios* file with colleagues.

To import and use the shared transformation scenario:
1. Go to **DITA Maps**>**Configure Transformation Scenarios**, right-click anywhere in the scenarios list, and select **Import scenarios**.
1. Select the relevant *.scenarios* file, and click **Open**.
1. Set **Storage** to **Global Options**, and click **Import**. The new transformation scenario appears in the scenario list.