---
title: IntelliSenseHostFlags | Документация Майкрософт
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980934"
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
  
|Участники|Описание|  
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
