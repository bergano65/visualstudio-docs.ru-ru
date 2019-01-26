---
title: IntelliSenseHostFlags | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 408b7a8ca4ea8a85dabe63d0871f622af68e6a97
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962853"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Указывает флаги узла IntelliSense.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
### <a name="parameters"></a>Параметры  
  
|Участники|Описание:|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Контекстный буфер доступен только для чтения.|  
|`IHF_NOSEPARATESUBJECT`|Нет текста темы. Буфер контекста содержит целевой объект IntelliSense (подразумевает `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Текст темы не многопроцессорного-строки с поддержкой.|  
|`IHF_FORCECOMMITTOCONTEXT`|Эквивалентно `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Изменения (в предмета или контекста) должны выполняться в режиме замены.|  
  
## <a name="requirements"></a>Требования  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop>