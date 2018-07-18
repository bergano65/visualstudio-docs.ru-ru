---
title: IntelliSenseHostFlags | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a096e79a64168f74150103a5f3ba3a8683fe184e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126761"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Задает флаги узла IntelliSense.  
  
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
  
#### <a name="parameters"></a>Параметры  
  
|Участники|Описание|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Контекст буфер доступен только для чтения.|  
|`IHF_NOSEPARATESUBJECT`|Нет текста для темы. Контекст буфер содержит целевой IntelliSense (подразумевает `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Текст темы не несколькими-строки поддерживает.|  
|`IHF_FORCECOMMITTOCONTEXT`|Эквивалентно `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Изменение (в теме или контекста) должны выполняться в режиме замены.|  
  
## <a name="requirements"></a>Требования  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop>