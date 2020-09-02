---
title: 'IDebugProcess2:: Name | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68026ed56aabd08f93588277c8d2b44e13604974
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723964"
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
Возвращает заголовок, понятное имя или имя файла процесса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName( 
   GETNAME_TYPE  gnType,
   BSTR*         pbstrName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE  gnType,
   out string         pbstrName
);
```

## <a name="parameters"></a>Параметры
`gnType`\
окне Значение из перечисления [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) , указывающее тип возвращаемого имени.

`pbstrName`\
заполняет Возвращает имя процесса.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
