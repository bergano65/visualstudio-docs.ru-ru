---
title: 'IDebugDocumentTextEvents2:: Онинсерттекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnInsertText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onInsertText
ms.assetid: 6040181f-7288-4a42-953c-d23f74200431
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6028a2859da79812440339adb3efbce6dd710b72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923058"
---
# <a name="idebugdocumenttextevents2oninserttext"></a>IDebugDocumentTextEvents2::onInsertText
Уведомляет пакет отладки, что текст вставлен в документ.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT onInsert( 
   TEXT_POSITION pos,
   DWORD         dwNumToInsert
);
```

```csharp
int onInsert( 
   enum_TEXT_POSITION pos,
   uint               dwNumToInsert
);
```

## <a name="parameters"></a>Параметры
`pos`\
окне Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , указывающая место вставки текста.

`dwNumToInsert`\
окне Указывает количество вставленных символов текста.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
