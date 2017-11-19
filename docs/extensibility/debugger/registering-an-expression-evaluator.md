---
title: "Регистрация вычислитель выражений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa0d368a68dcbacc2d8b137011efb5942429b7cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="registering-an-expression-evaluator"></a>Регистрация вычислитель выражений
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Средство оценки выражений (Эстония) должен зарегистрироваться как фабрика класса с среду Windows COM и Visual Studio. EE реализован в виде библиотеки DLL, чтобы он могут вноситься в адресное пространство ядра (DE) отладки или Visual Studio адресное пространство, в зависимости от того, который создает экземпляр сущности EE.  
  
## <a name="managed-code-expression-evaluator"></a>Вычислитель выражений управляемого кода  
 Управляемый код EE реализуется в виде библиотеки классов, который является библиотекой DLL, которая регистрирует себя среду COM, обычно начинается с помощью вызова Программа VSIP **regpkg.exe**. Фактический процесс записи реестра для среды COM обрабатывается автоматически.  
  
 Метод основного класса помечен атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, указывающее, что этот метод вызывается в том случае, когда библиотека DLL зарегистрирована в COM. Этот метод регистрации, часто называют `RegisterClass`, выполняющий задачу регистрации библиотеки DLL с помощью Visual Studio. Соответствующий `UnregisterClass` (помеченные <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), отменяет действия `RegisterClass` при удалении библиотеки DLL.  
  
 Те же записи реестра выполняются как для EE написано в неуправляемом коде; Единственное различие заключается в том, что нет вспомогательные функции например `SetEEMetric` для выполнения работы для вас. Пример этого процесса регистрации или отмены регистрации выглядит следующим образом:  
  
### <a name="example"></a>Пример  
 Эта функция показывает, как управляемый код EE регистрирует и отменяет регистрацию себя с помощью Visual Studio.  
  
```csharp  
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
  
## <a name="unmanaged-code-expression-evaluator"></a>Средство оценки выражений неуправляемого кода  
 Реализует EE DLL `DllRegisterServer` функции, чтобы зарегистрироваться в среде COM, а также Visual Studio.  
  
> [!NOTE]
>  MyCEE реестра примере кода можно найти в dllentry.cpp файл, расположенный в установку VSIP с EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>Серверный процесс для библиотеки DLL  
 При регистрации EE, сервер библиотеки DLL:  
  
1.  Регистрирует своей фабрики класса `CLSID` согласно обычным соглашениями COM.  
  
2.  Вызывает вспомогательную функцию `SetEEMetric` для регистрации с помощью Visual Studio EE метрики, показанные в следующей таблице. Функция `SetEEMetric` и метрики, указанным ниже являются частью библиотеки dbgmetric.lib. В разделе [SDK вспомогательные методы для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) подробные сведения.  
  
    |Метрика|Описание|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID`Класс фабрики EE|  
    |`metricName`|Имя EE как отображаемую строку|  
    |`metricLanguage`|Имя языка, который является EE предназначен для оценки|  
    |`metricEngine`|`GUID`s ядро отладки (DE), работающие с этой EE|  
  
    > [!NOTE]
    >  `metricLanguage``GUID` Определяет язык, имя, но он является `guidLang` аргумент `SetEEMetric` выбирает язык. Когда компилятор создает файла отладочной информации, следует писать соответствующего `guidLang` , чтобы DE известно, какие EE для использования. DE обычно запрашивают поставщика символов для данного языка `GUID`, который хранится в файла отладочной информации.  
  
3.  Регистрирует с Visual Studio, создав разделы в HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, где *X.Y* версия Visual Studio, чтобы зарегистрироваться.  
  
### <a name="example"></a>Пример  
 Эта функция показывает, как неуправляемый код (C++) EE регистрирует и отменяет регистрацию себя с помощью Visual Studio.  
  
```cpp  
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
  
## <a name="see-also"></a>См. также  
 [Написание выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)