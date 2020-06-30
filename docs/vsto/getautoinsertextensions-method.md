---
title: Метод GetAutoInsertExtensions
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5d88af6f24306b7b243359c9797a2cb7e7449bc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543511"
---
# <a name="getautoinsertextensions-method"></a>Метод GetAutoInsertExtensions
  Возвращает сведения о приложениях для Office, которые будут автоматически вставляться во время отладки.

 Этот метод зарезервирован для использования в будущем.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*псаекстенсионнамес*|Имена расширений приложений для Office.|

## <a name="return-value"></a>Возвращаемое значение
 Значение HRESULT, указывающее, успешно ли завершен метод.

## <a name="remarks"></a>Комментарии
 Каждое добавляемое приложение для Office возвращается как имя расширения приложения Office, которое соответствует значению в разделе **HKEY_CURRENT_USER \софтваре\микрософт\оффице\веф\девелопер**. Узел должен искать эти значения в реестре, а затем автоматически вставлять расширения.
