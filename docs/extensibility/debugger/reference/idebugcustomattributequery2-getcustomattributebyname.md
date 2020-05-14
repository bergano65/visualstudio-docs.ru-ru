---
title: IdebugCustomАтрибутАкери2::GetCustomАтрибутПоимен (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732563"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Получает пользовательские байты атрибутов с учетом названия пользовательского атрибута.

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
(в) Строка, содержащая имя пользовательского атрибута для поиска.

`ppBlob`\
(в, вне) Массив, заполненный пользовательскими байтами атрибута.

`pdwLen`\
(в, вне) Определяет максимальное количество байтов, чтобы `ppBlob` вернуться в массив, и возвращает количество байтов, фактически написанных в массив.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращает S_OK или возвращает S_FALSE, если пользовательский атрибут не существует. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Установите `ppBlob` параметр на нулевое значение, чтобы вернуть количество доступных байтов атрибутов. Затем выделите массив и передайте этот массив для `ppBlob` параметра.

 Байты атрибутов представляют необработанные данные пользовательского атрибута.

 Если `ppBlob` параметры `pdwLen` и параметры настроены на нулевую величину, этот метод может быть использован для определения того, существует ли просто пользовательский атрибут. Более простой альтернативой, однако, является вызов метода [IsCustomAttributeDefined.](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

## <a name="see-also"></a>См. также
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
