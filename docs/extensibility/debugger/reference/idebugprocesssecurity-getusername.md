---
title: 'Идебугпроцесссекурити:: имя_пользователя | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef00a0b7489c3e5cb709520546f3d3f26c8a4eba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723257"
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
