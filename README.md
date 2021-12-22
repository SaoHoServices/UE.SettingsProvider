# UE.SettingsProvider
SettingsProvider Plugin Documentation


For Example:  
  
UCLASS(Config = SettingsExample, DefaultConfig, Meta = (DisplayName = "SettingsExample"))  
class USettingsExample : public USettingsProvider  
{  
	GENERATED_UCLASS_BODY()  
	  
public:  
	static USettingsExample &Get();  
  
public:  
	UPROPERTY(Transient, EditAnywhere, Category = SettingsExample, Meta = (DisplayPriority = 0))  
	bool bGlobalSettings;  
  
public:  
	UPROPERTY(GlobalConfig, EditAnywhere, Category = SettingsExample)  
	FString ConfigTest;  
  
private:  
	UPROPERTY(Transient)  
	FString EngineConfigFile;  
  
	UPROPERTY(Transient)  
	FString ProjectConfigFile;  
  
public:  
	virtual FString GetConfigName() const override;  
	virtual void PreSaveSection() override;  
	virtual void PreLoadSection() override;  
};  
