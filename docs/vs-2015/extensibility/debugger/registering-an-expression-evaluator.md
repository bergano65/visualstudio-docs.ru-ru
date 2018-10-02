---
title: Регистрация вычислителя выражений | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 34cf96f38d169994d85f758c9453b6ad15ad6390
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560693"
---
# <a name="registering-an-expression-evaluator"></a>Регистрация вычислителя выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [регистрация вычислителя выражений](https://docs.microsoft.com/visualstudio/extensibility/debugger/registering-an-expression-evaluator).  
  
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Средство оценки выражений (EE) необходимо зарегистрировать себя в качестве фабрики класса со среды Windows COM и Visual Studio. EE реализовано как библиотеку DLL так, что он может внедряться в адресное пространство ядра (DE) отладки или адресное пространство Visual Studio, в зависимости от того, который создает экземпляр сущности EE.  
  
## <a name="managed-code-expression-evaluator"></a>Вычислитель выражений управляемого кода  
 Управляемый код, EE реализуется как библиотека классов, который представляет собой библиотеку DLL, которая регистрировала себя среды COM, обычно начинается с вызова к программе VSIP, **regpkg.exe**. Фактический процесс записи реестра для среды COM обрабатывается автоматически.  
  
 Метод основного класса помечен атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, указывающее, что этот метод вызывается в том случае, когда библиотека DLL зарегистрирована в COM. Этот метод регистрации, часто называют `RegisterClass`, выполняющий задачу регистрации библиотеки DLL с помощью Visual Studio. Соответствующий `UnregisterClass` (отмеченные <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), отменяет эффект `RegisterClass` при удалении библиотеки DLL.  
  
 Что касается EE, написанный в неуправляемом коде; выполняются те же записи реестра Единственное различие — это не вспомогательной функции например `SetEEMetric` для выполнения работы для вас. Пример этого процесса регистрации или ее отмены выглядит следующим образом:  
  
### <a name="example"></a>Пример  
 Эта функция показывает, как управляемый код EE регистрирует и отменяет свою регистрацию с помощью Visual Studio.  
  
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
 Реализует EE DLL `DllRegisterServer` функции для регистрации в среде COM, а также Visual Studio.  
  
> [!NOTE]
>  Пример реестра MyCEE кода кода можно найти в dllentry.cpp файл, который находится в VSIP установку с использованием EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>Процесс сервера библиотеки DLL  
 При регистрации EE, сервер библиотеки DLL:  
  
1.  Регистрирует своей фабрики класса `CLSID` согласно обычной соглашениями COM.  
  
2.  Вызывается вспомогательная функция `SetEEMetric` для регистрации с помощью Visual Studio EE метрик, отображаемых в таблице ниже. Функция `SetEEMetric` . они входят в состав библиотеки dbgmetric.lib метрик, указанных ниже. См. в разделе [вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) подробные сведения.  
  
    |Метрика|Описание|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` Класс фабрики EE|  
    |`metricName`|Имя EE как отображаемую строку|  
    |`metricLanguage`|Имя языка, именно EE предназначен для оценки|  
    |`metricEngine`|`GUID`s подсистемы отладки (DE), которые работают с этой EE|  
  
    > [!NOTE]
    >  `metricLanguage``GUID` Определяет язык, имя, но он является `guidLang` аргумент `SetEEMetric` , который выбирает язык. Когда компилятор формирует файла отладочной информации, он должен записывать соответствующий `guidLang` таким образом, чтобы DE знает, какие EE для использования. DE обычно запрашивают поставщик символов для данного языка `GUID`, который хранится в файле сведения отладки.  
  
3.  Регистрирует с помощью Visual Studio, создав ключи в разделе HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, где *X.Y* — это версия Visual Studio для регистрации.  
  
### <a name="example"></a>Пример  
 Эта функция показывает, каким образом неуправляемого кода (C++) EE регистрирует и отменяет свою регистрацию с помощью Visual Studio.  
  
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
  
## <a name="see-also"></a>См. также  
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

