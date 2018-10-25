---
title: IDebugDisassemblyStream2::Read | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7096d0e5bcb8f878c475db4f4c72a1a1aa7a7b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949192"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Считывает инструкциям, начиная с текущей позиции в потоке Дизассемблированный код.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwInstructions`  
 [in] Количество инструкций, чтобы дизассемблировать. Этот параметр также имеет максимальную длину `prgDisassembly` массива.  
  
 `dwFields`  
 [in] Сочетание флагов из [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) перечисления, которые указывают, какие поля `prgDisassembly` , для заполнения.  
  
 `pdwInstructionsRead`  
 [out] Возвращает число фактически дисассемблированный инструкции.  
  
 `prgDisassembly`  
 [out] Массив [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуры, заполняется Дизассемблированный код, одну структуру каждого дизассемблированное инструкции. Длина этого массива определяется `dwInstructions` параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Максимальное количество инструкций, доступных в текущей области можно получить, вызвав [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) метод.  
  
 Можно изменить текущую позицию, где следующей инструкции считывается из путем вызова [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) метод.  
  
 `DSF_OPERANDS_SYMBOLS` Можно добавить флаг `DSF_OPERANDS` флаг в `dwFields` параметр, чтобы указать, что при разборке инструкции следует использовать имена символов.  
  
## <a name="see-also"></a>См. также  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)

