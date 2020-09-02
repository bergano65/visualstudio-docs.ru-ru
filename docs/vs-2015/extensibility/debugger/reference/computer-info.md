---
title: COMPUTER_INFO | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7b5c49aea62ff1f7cb6416f7e02f7e7a3c0a166
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561745"
---
# <a name="computer_info"></a>COMPUTER_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает компьютер, на котором работает отладчик.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct tagCOMPUTER_INFO  
{  
    WORD wProcessorArchitecture;  
    WORD wSuiteMask;  
    DWORD dwOperatingSystemVersion;  
} COMPUTER_INFO;  
```  
  
```csharp  
public struct COMPUTER_INFO  
{  
    public ushort wProcessorArchitecture;  
    public ushort wSuiteMask;  
    public uint dwOperatingSystemVersion;  
}  
```  
  
## <a name="terms"></a>Термины  
 впроцессорарчитектуре  
 Определяет архитектуру микропроцессора.  
  
 всуитемаск  
 Определяет маску набора.  
  
 двоператингсистемверсион  
 Номер версии операционной системы.  
  
## <a name="remarks"></a>Remarks  
 Эта структура возвращается методом [жеткомпутеринфо](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: Мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [жеткомпутеринфо](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
