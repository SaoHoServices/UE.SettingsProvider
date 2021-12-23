# UE.SettingsProvider
SettingsProvider Plugin Documentation


// For Example:  
// Create a class that inherits from SettingsProvider:  
// The complete class can be downloaded in the GitHub repository
    
UCLASS(MinimalAPI, Config = SettingsExample, DefaultConfig, Meta = (DisplayName = "SettingsExample"))  
class USettingsExample : public USettingsProvider  
{  
	GENERATED_UCLASS_BODY()  
	  
public:  
	static USettingsExample &Get();  
  
public:  
	// Whether to use a global configuration file, multiple projects use the same configuration file
	UPROPERTY(Transient, EditAnywhere, Category = SettingsExample, Meta = (DisplayPriority = 0))  
	bool bGlobalSettings;  
};  
  
// Need an editor module  
// Include "SettingsPage" Module  
// For Example:  
virtual void StartupModule() final  
{  
	FSettingsPageCommands::Get().InstallProvider(GetMutableDefault<USettingsExample>(), "SettingsExample", NSLOCTEXT("SettingsExample", "SettingsExample", "SettingsExample"), NSLOCTEXT("SettingsExample", "SettingsExampleDescription", "Open Settings Example Editor"));  
}  
// Open the menu command of the independent editor will be added to the Toolbar.
