---
title: Регистрация оценщика экспрессии Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713198"
---
# <a name="register-an-expression-evaluator"></a>Регистрация оценщика выражений
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 Оценщик выражения (EE) должен зарегистрироваться как фабрика классов как с средой Windows COM, так и с Visual Studio. EE настроен как DLL так, что он вводится либо в отладку двигателя (DE) адресное пространство или визуальный Studio адресное пространство, в зависимости от того, какая сущность мгновенно EE.

## <a name="managed-code-expression-evaluator"></a>Оценщик управляемого выражения кода
 Управляемый код EE реализован как библиотека класса, которая является DLL, который регистрируется в среде COM, обычно начатый с вызова в программу VSIP, *regpkg.exe*. Фактический процесс написания ключей реестра для среды COM обрабатывается автоматически.

 Метод основного класса <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>отмечен, что указывает на то, что метод должен быть вызван, когда DLL регистрируется с COM. Этот метод регистрации, часто называемый, `RegisterClass`выполняет задачу регистрации DLL с Visual Studio. Соответствующий `UnregisterClass` <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>(отмеченный), отменяет эффекты, `RegisterClass` когда DLL не установлен.
Те же записи реестра сделаны, как для EE, написанного в неуправляемом коде; Разница лишь в том, что нет `SetEEMetric` функции помощника, например, чтобы сделать работу за вас. Ниже приводится пример процесса регистрации и нерегистрации.

### <a name="example"></a>Пример
 Следующая функция показывает, как управляемый код EE регистрируется и не регистрируется в Visual Studio.

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

## <a name="unmanaged-code-expression-evaluator"></a>Неуправляемый оценщик выражения кода
 EE DLL реализует `DllRegisterServer` функцию регистрации в среде COM, а также Visual Studio.

> [!NOTE]
> Вы можете найти образец кода MyCEE код реестра код в *файле dllentry.cpp*, который находится в установке VSIP под EnVSDK-MyCPkgs-MyCEE.

### <a name="dll-server-process"></a>Процесс dLL сервера
 При регистрации EE сервер DLL:

1. Регистрирует свою фабрику `CLSID` класса в рамках обычных конвенций COM.

2. Вызывает функцию `SetEEMetric` помощника, чтобы зарегистрироваться в Visual Studio метрикe EE, показанных в следующей таблице. Функция `SetEEMetric` и метрики, указанные следующим образом, являются частью библиотеки *dbgmetric.lib.* Подробнее о ней читайте в материале [помощников SDK.](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

    |Метрика|Описание|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`завода класса EE|
    |`metricName`|Название EE как отображаемая строка|
    |`metricLanguage`|Название языка, который EE предназначен для оценки|
    |`metricEngine`|`GUID`s отладки двигателей (DE), которые работают с этим EE|

    > [!NOTE]
    > Язык `metricLanguage``GUID` идентифицирует язык по имени, `guidLang` но `SetEEMetric` это аргумент, который выбирает язык. Когда компилятор генерирует файл информации об отладке, он должен написать соответствующий, `guidLang` чтобы DE знал, какой EE использовать. DE обычно запрашивает поставщика символов для этого языка, `GUID`который хранится в файле информации отладки.

3. Регистрируется в Visual Studio, создавая ключи под\\HKEY_LOCAL_MACHINE»SOFTWARE-Microsoft-VisualStudio*X.Y*, где *X.Y* является версией Visual Studio для регистрации.

### <a name="example"></a>Пример
 Следующая функция показывает, как неуправляемый код (КЗ) EE регистрируется и не регистрируется в Visual Studio.

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
- [Написание оценщика экспрессии CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Помощники SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
