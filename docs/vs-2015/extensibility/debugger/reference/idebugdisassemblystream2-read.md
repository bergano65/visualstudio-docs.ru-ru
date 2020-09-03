---
title: 'IDebugDisassemblyStream2:: Read | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 520c801a0603f2c6d3228ae95ad144827eac0088
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203007"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Считывает инструкции, начиная с текущей позицией в потоке дизассемблированного кода.  
  
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
 окне Количество инструкций для разсборки. Это значение также является максимальной длиной `prgDisassembly` массива.  
  
 `dwFields`  
 окне Сочетание флагов из перечисления [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) , которые указывают, какие поля должны `prgDisassembly` быть заполнены.  
  
 `pdwInstructionsRead`  
 заполняет Возвращает количество фактически собранных инструкций.  
  
 `prgDisassembly`  
 заполняет Массив структур [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md) , которые заполняются с помощью разсобранного кода, одной структуры на каждую разобранную инструкцию. Длина этого массива определяется `dwInstructions` параметром.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Максимальное количество инструкций, доступных в текущей области, можно получить, вызвав [метод метода](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) superscope.  
  
 Текущую позицию, из которой считывается следующая инструкция, можно изменить, вызвав метод [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .  
  
 `DSF_OPERANDS_SYMBOLS`Флаг можно добавить к `DSF_OPERANDS` флагу в `dwFields` параметре, чтобы указать, что при разсборке инструкций следует использовать имена символов.  
  
## <a name="see-also"></a>См. также:  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
