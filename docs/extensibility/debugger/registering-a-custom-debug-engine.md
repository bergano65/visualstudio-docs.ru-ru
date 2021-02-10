---
title: Регистрация пользовательского модуля отладки | Документация Майкрософт
description: Узнайте, как модуль отладки регистрирует себя в качестве фабрики классов, следуя соглашениям COM, а также с регистрацией в Visual Studio через реестр.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4581411a2601bf598762a7157f9df0e006995230
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961122"
---
# <a name="register-a-custom-debug-engine"></a>Регистрация пользовательского модуля отладки
Модуль отладки должен зарегистрировать себя в качестве фабрики класса, следуя соглашениям COM, а также регистрации в Visual Studio с помощью подраздела реестра Visual Studio.

> [!NOTE]
> Пример регистрации модуля отладки можно найти в образце Текстинтерпретер, который создается в составе [учебника: создание модуля отладки с помощью ATL com](/previous-versions/bb147024(v=vs.90)).

## <a name="dll-server-process"></a>Серверный процесс DLL
 Модуль отладки обычно настраивается в собственной библиотеке DLL как сервер COM. Таким образом, модуль отладки должен зарегистрировать идентификатор CLSID своей фабрики класса с помощью COM, прежде чем Visual Studio сможет получить к ней доступ. Затем модуль отладки должен зарегистрировать себя в Visual Studio для установки любых свойств (в других случаях известных как метрики), поддерживаемых ядром отладки. Выбор метрик, записываемых в подраздел реестра Visual Studio, зависит от функций, поддерживаемых подсистемой отладки.

 [Вспомогательные методы SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) описывают не только расположения реестра, необходимые для регистрации модуля отладки. Здесь также описывается библиотека *дбгметрик. lib* , которая содержит ряд полезных функций и деклараций для разработчиков на C++, которые упрощают управление реестром.

### <a name="example"></a>Пример
 В следующем примере (из примера Текстинтерпретер) показано, как использовать `SetMetric` функцию (из *дбгметрик. lib*) для регистрации модуля отладки в Visual Studio. Передаваемые метрики также определяются в *дбгметрик. lib*.

> [!NOTE]
> Текстинтерпретер — это базовый модуль отладки; Он не настраивается, и, следовательно, не регистрирует никаких других функций. Более полный модуль отладки будет иметь целый список `SetMetric` вызовов или их эквивалент, по одному для каждого компонента, поддерживаемого ядром отладки.

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

## <a name="see-also"></a>См. также раздел
- [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Вспомогательные методы SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Учебник. Создание модуля отладки с помощью ATL COM](/previous-versions/bb147024(v=vs.90))