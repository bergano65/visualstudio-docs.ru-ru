---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d874a00c3c82108c224f18922f2b4853279beaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322205"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Получает настраиваемые атрибуты байтов, заданному имени настраиваемого атрибута.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>Параметры
`pszCustomAttributeName`\
[in] Строка, содержащая имя настраиваемого атрибута для поиска.

`ppBlob`\
[in, out] Массив, который заполняется байты настраиваемого атрибута.

`pdwLen`\
[in, out] Указывает максимальное число байтов для возврата в `ppBlob` массива и возвращает количество байтов, фактически записанных в массив.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK, или возвращает S_FALSE, если настраиваемый атрибут не существует. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Задайте `ppBlob` параметр в значение null для возврата количества атрибутов доступных байтов. Затем выделить память для массива и передать этот массив в для `ppBlob` параметра.

 Атрибут байты представляют необработанные данные настраиваемого атрибута.

 Если `ppBlob` и `pdwLen` присвоено значение null, этот метод можно использовать для определения того, существует ли просто настраиваемого атрибута. Тем не менее, простой альтернативой является вызов [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) метод.

## <a name="see-also"></a>См. также
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)