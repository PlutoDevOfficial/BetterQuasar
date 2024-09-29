# BetterQuasar
A fork of the newest version of the Popular Remote Administration Tool Quasar with some improvements made to it´s server and client

## Changes

Better Quasar (QuasarX)
```
// Token: 0x06000629 RID: 1577 RVA: 0x00028994 File Offset: 0x00026B94
		public void Build()
		{
			using (AssemblyDefinition assemblyDefinition = AssemblyDefinition.ReadAssembly(this._clientFilePath))
			{
				this.WriteSettings(assemblyDefinition);
				assemblyDefinition.Write(this._options.OutputPath);
			}
			if (this._options.AssemblyInformation != null)
			{
				VersionResource versionResource = new VersionResource();
				versionResource.LoadFrom(this._options.OutputPath);
				versionResource.FileVersion = this._options.AssemblyInformation[7];
				versionResource.ProductVersion = this._options.AssemblyInformation[6];
				versionResource.Language = 0;
				StringFileInfo stringFileInfo = (StringFileInfo)versionResource["StringFileInfo"];
				stringFileInfo["CompanyName"] = this._options.AssemblyInformation[2];
				stringFileInfo["FileDescription"] = this._options.AssemblyInformation[1];
				stringFileInfo["ProductName"] = this._options.AssemblyInformation[0];
				stringFileInfo["LegalCopyright"] = this._options.AssemblyInformation[3];
				stringFileInfo["LegalTrademarks"] = this._options.AssemblyInformation[4];
				stringFileInfo["ProductVersion"] = versionResource.ProductVersion;
				stringFileInfo["FileVersion"] = versionResource.FileVersion;
				stringFileInfo["Assembly Version"] = versionResource.ProductVersion;
				stringFileInfo["InternalName"] = this._options.AssemblyInformation[5];
				stringFileInfo["OriginalFilename"] = this._options.AssemblyInformation[5];
				versionResource.SaveTo(this._options.OutputPath);
			}
			if (!string.IsNullOrEmpty(this._options.IconPath))
			{
				new IconDirectoryResource(new IconFile(this._options.IconPath)).SaveTo(this._options.OutputPath);
			}
   ```

Original

```
		// Token: 0x0600052E RID: 1326 RVA: 0x000269AC File Offset: 0x00024BAC
		public void Build()
		{
			using (AssemblyDefinition assemblyDefinition = AssemblyDefinition.ReadAssembly(this._clientFilePath))
			{
				this.WriteSettings(assemblyDefinition);
				Renamer renamer = new Renamer(assemblyDefinition);
				if (!renamer.Perform())
				{
					throw new Exception("renaming failed");
				}
				renamer.AsmDef.Write(this._options.OutputPath);
			}
			if (this._options.AssemblyInformation != null)
			{
				VersionResource versionResource = new VersionResource();
				versionResource.LoadFrom(this._options.OutputPath);
				versionResource.FileVersion = this._options.AssemblyInformation[7];
				versionResource.ProductVersion = this._options.AssemblyInformation[6];
				versionResource.Language = 0;
				StringFileInfo stringFileInfo = (StringFileInfo)versionResource["StringFileInfo"];
				stringFileInfo["CompanyName"] = this._options.AssemblyInformation[2];
				stringFileInfo["FileDescription"] = this._options.AssemblyInformation[1];
				stringFileInfo["ProductName"] = this._options.AssemblyInformation[0];
				stringFileInfo["LegalCopyright"] = this._options.AssemblyInformation[3];
				stringFileInfo["LegalTrademarks"] = this._options.AssemblyInformation[4];
				stringFileInfo["ProductVersion"] = versionResource.ProductVersion;
				stringFileInfo["FileVersion"] = versionResource.FileVersion;
				stringFileInfo["Assembly Version"] = versionResource.ProductVersion;
				stringFileInfo["InternalName"] = this._options.AssemblyInformation[5];
				stringFileInfo["OriginalFilename"] = this._options.AssemblyInformation[5];
				versionResource.SaveTo(this._options.OutputPath);
			}
			if (!string.IsNullOrEmpty(this._options.IconPath))
			{
				new IconDirectoryResource(new IconFile(this._options.IconPath)).SaveTo(this._options.OutputPath);
			}
		}
```
