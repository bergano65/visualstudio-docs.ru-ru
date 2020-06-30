---
title: Интерфейс IWefDebuggingSupport
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
ms.openlocfilehash: 0a4883d36c1833c66a2539380184521b070f5c2a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544733"
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
