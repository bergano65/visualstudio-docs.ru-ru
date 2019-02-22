---
title: Интерфейс IWefDebuggingSupport
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a71adf5371275fbbdc19cdf09be96ef900ec073d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599718"
---
# <a name="iwefdebuggingsupport-interface"></a>Интерфейс IWefDebuggingSupport
  Реализуется отладочной среде, такой как Visual Studio, чтобы упростить отладку приложений для Office. Приложение Office, например Word или Excel, получает этот интерфейс из Visual Studio и затем вызывает методы в интерфейсе в определенных точках во время сеанса отладки.

## <a name="syntax"></a>Синтаксис

```csharp
[
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),
    oleautomation
]
interface IWefDebuggingSupport : IUnknown
{
    HRESULT SetWefProcessId(
        [in] DWORD dwProcessId);
    HRESULT GetAutoInsertExtensions(
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);
}
```

## <a name="methods"></a>Методы
 В следующей таблице перечислены методы, которые определяет этот интерфейс IWefDebuggingSupport.

|name|Описание|
|----------|-----------------|
|[Метод GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Получает сведения о приложениях для Office, который автоматически вставляются во время отладки.|
|[Метод SetWefProcessId](../vsto/setwefprocessid-method.md)|Предоставляет идентификатор процесса, в которой выполняются расширения Framework Web (WEF) содержимое.|
