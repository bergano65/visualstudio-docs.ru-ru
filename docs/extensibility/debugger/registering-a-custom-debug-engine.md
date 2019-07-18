---
title: Регистрация пользовательского модуля отладки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90400a9bf750eb80e40d6558fed382e18e7824ef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316048"
---
# <a name="register-a-custom-debug-engine"></a>Регистрация пользовательского модуля отладки
Модуль отладки необходимо зарегистрировать себя в качестве фабрики класса, следующие соглашения COM, а также регистрировать с помощью Visual Studio через подраздел реестра Visual Studio.

> [!NOTE]
> Вы найдете пример, как зарегистрировать модуль отладки в образце TextInterpreter, являющуюся частью [руководства: Создание модуля отладки с помощью ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).

## <a name="dll-server-process"></a>Процесс сервера библиотеки DLL
 Модуль отладки обычно настраивается в собственную библиотеку DLL как COM-сервера. Таким образом модуль отладки необходимо зарегистрировать идентификатор CLSID своей фабрики класса COM прежде, чем доступ к нему Visual Studio. Затем модуль отладки должен зарегистрироваться с помощью Visual Studio, чтобы установить какие-либо свойства (в противном случае называется метрики) отладки ядра поддерживает. Выбор метрик, записанных в подраздел реестра Visual Studio зависит от возможностей, которые поддерживает модуль отладки.

 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) описывает не только разделы реестра, необходимые для регистрации модуля отладки; в ней также описывается *dbgmetric.lib* библиотеку, которая содержит ряд полезных функций и объявления для разработчиков C++, которые делают с управлением реестром проще.

### <a name="example"></a>Пример
 В следующем примере (из примера TextInterpreter) показано, как использовать `SetMetric` функции (из *dbgmetric.lib*), чтобы зарегистрировать модуль отладки в Visual Studio. Метрики, передаваемые также определены в *dbgmetric.lib*.

> [!NOTE]
> TextInterpreter — это механизм основные отладки; он не настроен и поэтому не регистрирует — любые другие компоненты. Более полный модуль отладки будет иметь полный список `SetMetric` поддерживает вызовы или их эквиваленты, один для каждого компонента обработчика отладки.

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
- [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Учебник. Создание модуля отладки с помощью ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)