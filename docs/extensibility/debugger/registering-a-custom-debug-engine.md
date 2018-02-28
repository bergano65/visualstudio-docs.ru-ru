---
title: "Регистрация пользовательского модулю отладки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 50903d9b45828725da03c0fcb0db0f08d7f884eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-custom-debug-engine"></a>Регистрация модулем отладки
Модуль отладки необходимо зарегистрировать себя в качестве фабрики класса COM соглашениям, а также регистрировать с помощью Visual Studio через раздел реестра Visual Studio.  
  
> [!NOTE]
>  Пример того, как зарегистрировать модуль отладки можно найти в образце TextInterpreter, являющуюся частью [учебника: построение отладку ядра с помощью ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Процесс сервера библиотеки DLL  
 Как правило модуль отладки реализуется в собственную DLL как COM-сервера. Это означает, что до Visual Studio можно получить доступ к модуль отладки необходимо зарегистрировать идентификатор CLSID своей фабрики класса COM. Затем отладчик должен зарегистрироваться с Visual Studio для установки всех свойств (в противном случае называется метрик) отладки поддерживает модуль. Выбор метрик, которые записываются в раздел реестра Visual Studio для ядра отладки зависит от функций, которые поддерживает модуль отладки.  
  
 [Вспомогательные функции пакета SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) описывает не только разделы реестра, необходимые для регистрации модуля отладки; он также описывает библиотеку dbgmetric.lib, которая содержит ряд полезных функций и объявления для разработчиков C++, которые делают с управлением реестром проще.  
  
### <a name="example"></a>Пример  
 Ниже приведен типичный (из примера TextInterpreter) описывает использование `SetMetric` функции (из dbgmetric.lib), чтобы зарегистрировать модуль отладки в Visual Studio. Метрики, передаваемые в dbgmetric.lib также определены.  
  
> [!NOTE]
>  TextInterpreter представляет собой модуль на основные отладки; не реализован и поэтому не регистрирует — любые другие компоненты. Более полный модуля отладки будет иметь полный список `SetMetric` поддерживает вызовы или их эквиваленты, один для каждого из компонентов ядра отладки.  
  
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
  
## <a name="see-also"></a>См. также  
 [Создание модулем отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Вспомогательные функции пакета SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Учебник: Создание модуля отладки с использованием ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)