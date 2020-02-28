**DESCRIPTION**

The CSP Development Suite is a tool created by Microsoft to help with creating custom Configuration Service Providers (CSPs). You can quickly create SyncML profiles using DDF (definition) files. Download the DDF files for your Windows 10 build, then import this into the CSP Dev Suite.

- Run **CSPDevelopmentSuite.exe**
- Select **the SyncML Generator Tool**
- Click **Open, File, Import DDF** to import your DDF for the CSP
- Obtain more info on how to enter values into each node by gathering more info on the CSP at https://aka.ms/CSPList
- Copy and paste the SyncML only including the ```<CmdID>1</CmdID>``` **Exec, Add, or Replace** tags into **Notepad++**
- Add ```<Atomic>``` to the top and ```</Atomic>``` to the end of the custom XML file.
- Replace all ```CmdID>1</CmdID>``` or that contain a followup number with ```<CmdID>_cmdid_</CmdID>``` as Citrix Endpoint Management will automaticly generated the numbering.

**Example code generate by SyncML Generator**
```
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/Personalization/DesktopImageUrl
          </LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">chr</Format>
          <Type>text/plain</Type>
        </Meta>
        <Data>http://example.com/jjvlebon/Wallpaper/desktopimage.jpeg</Data>
      </Item>
    </Replace>
    <Final/> 
  </SyncBody>
</SyncML>
```
**Final XML code ready to be used with Citrix Endpoint Management**
```
<Atomic>
  <CmdID>_cmdid_</CmdID>
    <Replace>
      <CmdID>_cmdid_</CmdID>
        <Item>
          <Target>
             <LocURI>./Vendor/MSFT/Personalization/DesktopImageUrl</LocURI>
          </Target>
            <Meta>
               <Format xmlns="syncml:metinf">chr</Format>
               <Type>text/plain</Type>
           </Meta>
               <Data>http://example.com/jjvlebon/Wallpaper/desktopimage.jpeg</Data>
        </Item>
    </Replace>
</Atomic>
```
- Optionally export your SyncML for later reference.
- To deploy this sample, navigate to **Configure > Device Policies > Add > Filer on Windows Desktop/Tablet > Custom > Custom XML > Clear All > Select Windows Desktop/Tablet > Provide Policy Name** , then copy and paste the edited SyncML into the box and publish the CSP.

**Resources**

CSP Documentation: 
https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference?redirectedfrom=MSDN

CSP DDF Files: 
https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference?redirectedfrom=MSDN#csp-ddf-files-download 
Or download them from this GitHub Repository
