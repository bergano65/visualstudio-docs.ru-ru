---
title: Регистрация пользовательского модуля отладки | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 336320efce371d555854784e5fbbc60174340e03
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303502"
---
# <a name="registering-a-custom-debug-engine"></a>Регистрация пользовательского модуля отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Модуль отладки необходимо зарегистрировать себя в качестве фабрики класса COM соглашениям, а также регистрировать с помощью Visual Studio через подраздел реестра Visual Studio.  
  
> [!NOTE]
>  Пример того, как зарегистрировать модуль отладки можно найти в образце TextInterpreter, которая построена как часть [руководство: создание отладку ядра с помощью ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Процесс сервера библиотеки DLL  
 Как правило модуль отладки реализуется в собственную библиотеку DLL как COM-сервера. Это означает, что прежде чем Visual Studio можно получить доступ к модуль отладки необходимо зарегистрировать идентификатор CLSID своей фабрики класса COM. Затем модуль отладки должен зарегистрироваться с самой среды Visual Studio для того чтобы установить какие-либо свойства (в противном случае называется метрики) отладки ядра поддерживает. Выбор метрик, записываются в подраздел реестра Visual Studio для обработчика отладки зависит от возможностей, которые поддерживает модуль отладки.  
  
 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) описывает не только разделы реестра, необходимые для регистрации модуля отладки; он также описывает dbgmetric.lib библиотеку, которая содержит ряд полезных функций и объявления для разработчиков C++, которые делают с управлением реестром проще.  
  
### <a name="example"></a>Пример  
 Ниже приведен типичный пример (из примера TextInterpreter), демонстрирующий использование `SetMetric` функции (из dbgmetric.lib), для регистрации модуля отладки в Visual Studio. Метрики, передаваемые в dbgmetric.lib также определены.  
  
> [!NOTE]
>  TextInterpreter — это механизм основные отладки; он не реализует и поэтому не регистрируются, любые другие компоненты. Более полный модуль отладки будет иметь полный список `SetMetric` поддерживает вызовы или их эквиваленты, один для каждого компонента обработчика отладки.  
  
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
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Учебник: Создание модуля отладки с помощью ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)

