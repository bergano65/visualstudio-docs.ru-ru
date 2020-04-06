---
title: IntelliSenseHostFlags Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0df05e7363db01bd4f16fee5d75141dc93df1c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710272"
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

|Участники|Описание|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Буфер контекста читается только для чтения.|
|`IHF_NOSEPARATESUBJECT`|Нет текста темы. Контекстный буфер содержит цель IntelliSense (подразумевается). `!IHF_READONLYCONTEXT`|
|`IHF_SINGLELINESUBJECT`|Текст темы не является многолинейным.|
|`IHF_FORCECOMMITTOCONTEXT`|Эквивалентно `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|Редактирование (в предмете или контексте) должно осуществляться в режиме овертипа.|

## <a name="requirements"></a>Требования
 SingleFileeditor.idl

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.TextManager.Interop>
