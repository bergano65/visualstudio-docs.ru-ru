---
title: IDebugDocumentTextEvents2::onDestroy | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnDestroy
helpviewer_keywords:
- IDebugDocumentTextEvents2::onDestroy
ms.assetid: 60e4689c-c899-4c14-9d18-96393b741e1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ade70ce0f72d2f3b86d6f7ec95a61b4bad57b102
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685187"
---
# <a name="idebugdocumenttextevents2ondestroy"></a>IDebugDocumentTextEvents2::onDestroy
Указывает, что весь документ был удален.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT onDestroy( 
   void 
);
```

```csharp
int onDestroy();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)