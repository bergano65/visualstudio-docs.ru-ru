---
title: Интеллисенсехостфлагс | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12945998b215e9082591fad514bd9c16ab789405
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203893"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает флаги узла IntelliSense.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Элементы|Описание|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Буфер контекста доступен только для чтения.|  
|`IHF_NOSEPARATESUBJECT`|Нет текста темы. Буфер контекста содержит IntelliSense-Target (подразумевается `!IHF_READONLYCONTEXT` ).|  
|`IHF_SINGLELINESUBJECT`|Текст темы не поддерживает несколько строк.|  
|`IHF_FORCECOMMITTOCONTEXT`|Эквивалентно `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Редактирование (в теме или контексте) должно выполняться в режиме переввода.|  
  
## <a name="requirements"></a>Требования  
 Синглефилидитор. idl  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
