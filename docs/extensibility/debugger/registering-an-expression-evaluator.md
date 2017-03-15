---
title: "Регистрация вычислитель выражений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [отладка SDK], вычисление выражений"
  - "вычислители выражений, регистрация"
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Регистрация вычислитель выражений
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Вычислитель выражений \(EE\) должен зарегистрироваться как фабрика класса с среду Windows COM и Visual Studio. EE реализуется как библиотека DLL, таким образом, он может вставить в адресное пространство ядра \(DE\) отладки или адресное пространство Visual Studio, в зависимости от того, который создает экземпляр сущности EE.  
  
## Вычислитель выражений управляемого кода  
 Управляемый код EE реализуется в виде библиотеки классов, который является библиотекой DLL, которая регистрирует себя в среде COM, обычно начинались с помощью вызова программе VSIP, **regpkg.exe**. Процесс записи реестра для среды COM обрабатывается автоматически.  
  
 Метод основного класса помечен атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, указывающую, что этот метод вызывается в том случае, когда библиотека DLL зарегистрирована в COM. Этот метод регистрации, часто называют `RegisterClass`, выполняющий задачу регистрации библиотеки DLL с помощью Visual Studio. Соответствующий `UnregisterClass` \(отмеченные <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>\), отменяет последствия `RegisterClass` при удалении библиотеки DLL.  
  
 Что касается EE, написанных неуправляемым кодом; выполняются те же записи реестра Единственным отличием, что существует не вспомогательной функции такие как `SetEEMetric` для выполнения работы для вас. Пример этого процесса регистрации и отмены регистрации выглядит следующим образом:  
  
### Пример  
 Эта функция показывает, как управляемый код EE регистрирует и отменяет свою регистрацию с помощью Visual Studio.  
  
```c#  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## Вычислитель выражений неуправляемого кода  
 Реализует EE DLL `DllRegisterServer` функции, чтобы зарегистрироваться в среде COM, а также Visual Studio.  
  
> [!NOTE]
>  Пример реестра MyCEE кода можно найти в dllentry.cpp файл, расположенный в установку VSIP EnVSDK\\MyCPkgs\\MyCEE.  
  
### Процесс сервера библиотеки DLL  
 При регистрации EE, сервер библиотеки DLL:  
  
1.  Регистрирует его фабрики класса `CLSID` согласно обычной соглашениями COM.  
  
2.  Вызывает вспомогательную функцию `SetEEMetric` для регистрации с помощью Visual Studio EE метрики, показано в следующей таблице. Функция `SetEEMetric` и метрики, указанными ниже являются частью библиотеки dbgmetric.lib. Подробные сведения см. в разделе [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
    |Метрика|Описание|  
    |-------------|--------------|  
    |`metricCLSID`|`CLSID` Класс фабрики EE|  
    |`metricName`|Имя EE как отображаемую строку|  
    |`metricLanguage`|Имя языка, который является EE предназначен для оценки|  
    |`metricEngine`|`GUID`s ядро отладки \(DE\), работающие с этой EE|  
  
    > [!NOTE]
    >  `metricLanguage` `GUID` Определяет язык, имя, но он является `guidLang` аргумент `SetEEMetric` который выбирает язык. Когда компилятор создает файл сведения для отладки, следует написать соответствующий `guidLang` чтобы DE знает, какие EE для использования. DE обычно запрашивают поставщика символов для данного языка `GUID`, который хранится в файле отладочной информации.  
  
3.  Регистрирует с помощью Visual Studio, создав ключи в разделе HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*X.Y*, где *X.Y* версия Visual Studio для регистрации.  
  
### Пример  
 Эта функция показывает, как неуправляемый код \(C\+\+\) EE регистрирует и отменяет свою регистрацию с помощью Visual Studio.  
  
```cpp#  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## См. также  
 [Написание вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)