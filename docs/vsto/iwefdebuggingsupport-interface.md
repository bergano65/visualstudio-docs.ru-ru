---
title: Интерфейс IWefDebuggingSupport
description: Узнайте, как можно использовать среду отладки, например Visual Studio, для упрощения отладки приложений Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a818973bdc2f62194d6ed0026c0798806fe5f2a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525326"
---
# <a name="iwefdebuggingsupport-interface"></a>Интерфейс IWefDebuggingSupport
  Реализуется средой отладки, например Visual Studio, для упрощения отладки приложений для Office. Приложение Office, например Word или Excel, получает этот интерфейс из Visual Studio, а затем вызывает методы интерфейса в определенных точках во время сеанса отладки.

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
 В следующей таблице перечислены методы, определяемые интерфейсом IWefDebuggingSupport.

|Имя|Описание|
|----------|-----------------|
|[Метод GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Возвращает сведения о приложениях для Office, которые будут автоматически вставляться во время отладки.|
|[Метод SetWefProcessId](../vsto/setwefprocessid-method.md)|Предоставляет идентификатор процесса, который будет запускать содержимое платформы веб-расширений (WEF).|
