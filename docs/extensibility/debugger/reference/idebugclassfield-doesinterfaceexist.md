---
title: Идебугклассфиелд::D Оесинтерфацеексист | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba732b698f7372772142fda73e71d9e22aa443a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734495"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Определяет, определен ли в классе определенный интерфейс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>Параметры
`pszInterfaceName`\
окне Строка, содержащая искомое имя интерфейса.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK, если интерфейс не существует, возвращает значение S_FALSE. в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод в силе возвращает перечисление всех интерфейсов и выполняет поиск соответствующего интерфейса в списке.

## <a name="see-also"></a>См. также раздел
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
