---
title: Метод GetAutoInsertExtensions
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
ms.openlocfilehash: fb767ec7301a1d4e0f29003971b017339228fc9f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611182"
---
# <a name="getautoinsertextensions-method"></a>Метод GetAutoInsertExtensions
  Получает сведения о приложениях для Office, который автоматически вставляются во время отладки.

 Этот метод зарезервирован для использования в будущем.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Параметры

|Параметр|Описание:|
|---------------|-----------------|
|*psaExtensionNames*|Имена расширений приложений для Office.|

## <a name="return-value"></a>Возвращаемое значение
 Значение HRESULT, указывающее, успешно ли завершен метод.

## <a name="remarks"></a>Примечания
 Каждое приложение для Office, вставляемый возвращается как имя расширения приложения Office, который соответствует значению в разделе **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. Узел должен искать эти значения в реестре и автоматически вставлять расширения.
