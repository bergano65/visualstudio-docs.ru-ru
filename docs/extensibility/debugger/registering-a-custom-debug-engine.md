---
title: Регистрация пользовательского двигателя отугивания (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713213"
---
# <a name="register-a-custom-debug-engine"></a>Регистрация пользовательского двигателя отладки
Двигатель отладки должен зарегистрироваться в качестве фабрики класса, следуя конвенциям COM, а также зарегистрироваться в Visual Studio через подключку реестра Visual Studio.

> [!NOTE]
> Вы можете найти пример того, как зарегистрировать отладку двигателя в образец TextInterpreter, который построен в рамках [учебника: Строительство двигателя отладки с помощью ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).

## <a name="dll-server-process"></a>Процесс dLL сервера
 Двигатель отладки обычно настраивается в своем собственном DLL в качестве сервера COM. Таким образом, отладка двигатель должен зарегистрировать CLSID своего класса завода с COM, прежде чем Visual Studio может получить к нему доступ. Затем движок отладки должен зарегистрироваться в Visual Studio, чтобы установить любые свойства (иначе известные как метрики) поддержки двигателя отладки. Выбор метрик, записанных в подключку реестра Visual Studio, зависит от особенностей, которые поддерживает движок отладки.

 [Помощники SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) описывают не только места регистрации реестра, необходимые для регистрации двигателя отладки; в ней также описывается библиотека *dbgmetric.lib,* которая содержит ряд полезных функций и деклараций для разработчиков СЗ, которые облегчают манипулирование реестром.

### <a name="example"></a>Пример
 В следующем примере (из образца TextInterpreter) показано, как использовать `SetMetric` функцию (от *dbgmetric.lib),* чтобы зарегистрировать движок отладки с Visual Studio. Пройденных метрик также определяются на *dbgmetric.lib.*

> [!NOTE]
> TextInterpreter является основным движком отладки; он не настраивается и, следовательно, не регистрируется- любые другие функции. Более полный отладка двигателя будет `SetMetric` иметь целый список вызовов или их эквивалент, по одному для каждой функции отладки двигателя поддерживает.

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
- [Создание пользовательского движка отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Помощники SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Учебник: Создание двигателя отладки с использованием ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
