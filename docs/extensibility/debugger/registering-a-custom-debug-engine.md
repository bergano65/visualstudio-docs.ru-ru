---
title: "Регистрация пользовательские отладки ядра | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладчики, регистрация"
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Регистрация пользовательские отладки ядра
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отладчик должен зарегистрироваться как фабрика класса следующие соглашения по COM, а также зарегистрировать в Visual Studio через подраздел реестра Visual Studio.  
  
> [!NOTE]
>  Пример регистрации модуля отладки можно найти в образце TextInterpreter создана как часть [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/ru-ru/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## Процесс сервера библиотеки DLL  
 Как правило ядра отладки реализуется в собственную библиотеку DLL как COM\-сервера. Это означает, что до Visual Studio можно получить доступ к ядра отладки необходимо зарегистрировать идентификатор CLSID его фабрики класса COM. Затем отладчик должен зарегистрироваться с помощью Visual Studio для установления любые свойства \(в противном случае называется метрик\) отладки ядра поддерживает. Выбор метрики, которые записываются в подраздел реестра Visual Studio для отладки ядра, зависит от возможностей, поддерживаемых ядра отладки.  
  
 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Описывает не только разделы реестра, необходимые для регистрации модуля отладки; Он также описывает библиотеку dbgmetric.lib, которая содержит ряд полезных функций и объявления для разработчиков C\+\+, которые делают управления реестром проще.  
  
### Пример  
 Ниже приведен типичный пример \(из примера TextInterpreter\) описывает использование `SetMetric` функции \(из dbgmetric.lib\), чтобы зарегистрировать модуль отладки в Visual Studio. Метрики, передаваемых в dbgmetric.lib также определены.  
  
> [!NOTE]
>  TextInterpreter – это механизм основные отладки; не реализован и поэтому не регистрирует — другие компоненты. Более полный ядра отладки будет иметь полный список `SetMetric` поддерживает вызовы или их эквивалент, один для каждого из компонентов ядра отладки.  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## См. также  
 [Создание пользовательские отладки ядра](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/ru-ru/9097b71e-1fe7-48f7-bc00-009e25940c24)