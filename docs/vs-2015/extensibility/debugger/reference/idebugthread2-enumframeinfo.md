---
title: 'IDebugThread2:: Енумфрамеинфо | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efda31daae198befbda35803ef71e1d0322e9bbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153085"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает список кадров стека для этого потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFieldSpec`  
 окне Сочетание флагов из перечисления [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) , которое указывает, какие поля структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) должны быть заполнены. Укажите `FIF_FUNCNAME_FORMAT` флаг для форматирования имени функции в одной строке.  
  
 `nRadix`  
 окне Основание системы счисления, используемое для форматирования числовых данных в перечислителе.  
  
 `ppEnum`  
 заполняет Возвращает объект [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) , содержащий список структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) , описывающих кадр стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Фреймы потока перечисляются по порядку, а текущий фрейм перечислится первыми, а самый старый кадр перечисляется последним.  
  
## <a name="see-also"></a>См. также:  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
