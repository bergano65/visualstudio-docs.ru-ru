---
title: 'Идебугпроцесссекурити:: имя_пользователя | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 075cc96866a2b7b4a987c04c6cb78dcd22da2b50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912029"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Возвращает имя пользователя от поставщика порта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Параметры
`pbstrUserName`\
заполняет Строка, содержащая имя пользователя.

## <a name="return-value"></a>Возвращаемое значение
 Если метод завершается успешно, возвращает значение `S_OK`. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 `GetUserName` Возвращает имя пользователя, отображаемое в столбце **имя пользователя** диалогового окна **Присоединение к процессу** . Чтобы открыть диалоговое окно **Присоединение к процессу** , щелкните **присоединить к процессу** в меню **Сервис** в [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE).

## <a name="see-also"></a>См. также раздел
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
