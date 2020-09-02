---
title: Идебугпортпиккер::D Исплайпортпиккер | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dd9317a73800a3886a5a807e9e28b0c24b2301c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188382"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Отображает указанное диалоговое окно, позволяющее пользователю выбрать порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `hwndParentDialog`  
 окне Обработчик для родительского диалогового окна.  
  
 `pbstrPortId`  
 заполняет Строка идентификатора порта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращаемое значение `S_FALSE` (или возвращаемое значение со значением `S_OK` `BSTR` `NULL` ) указывает, что пользователь щелкнул кнопку **Отмена**.  
  
## <a name="see-also"></a>См. также:  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
