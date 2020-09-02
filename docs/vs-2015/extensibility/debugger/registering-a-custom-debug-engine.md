---
title: Регистрация пользовательского модуля отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703602"
---
# <a name="registering-a-custom-debug-engine"></a>Регистрация пользовательского модуля отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Модуль отладки должен зарегистрировать себя как фабрику класса, следуя соглашениям COM, а также зарегистрировать в Visual Studio с помощью подраздела реестра Visual Studio.  
  
> [!NOTE]
> Пример регистрации модуля отладки можно найти в образце Текстинтерпретер, который создается в составе [учебника: создание модуля отладки с помощью ATL com](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Серверный процесс DLL  
 Как правило, модуль отладки реализуется в собственной библиотеке DLL как сервер COM. Это означает, что модуль отладки должен зарегистрировать CLSID своей фабрики класса с COM, прежде чем Visual Studio сможет получить к ней доступ. Затем модуль отладки должен зарегистрировать себя в Visual Studio, чтобы установить любые свойства (в других случаях называемые метриками), поддерживаемые ядром отладки. Выбор метрик, которые записываются в подраздел реестра Visual Studio для модуля отладки, зависит от функций, поддерживаемых подсистемой отладки.  
  
 [Вспомогательные методы SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) описывают не только расположения реестра, необходимые для регистрации модуля отладки. Здесь также описывается библиотека дбгметрик. lib, которая содержит ряд полезных функций и деклараций для разработчиков на C++, которые упрощают управление реестром.  
  
### <a name="example"></a>Пример  
 Ниже приведен типичный пример (из примера Текстинтерпретер), демонстрирующий использование `SetMetric` функции (из дбгметрик. lib) для регистрации модуля отладки в Visual Studio. Передаваемые метрики также определяются в дбгметрик. lib.  
  
> [!NOTE]
> Текстинтерпретер — это базовый модуль отладки; Он не реализуется, и, следовательно, не регистрирует никаких других функций. Более полный модуль отладки будет иметь целый список `SetMetric` вызовов или их эквивалент, по одному для каждого компонента, поддерживаемого ядром отладки.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Вспомогательные методы SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Учебник. Создание модуля отладки с помощью ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
