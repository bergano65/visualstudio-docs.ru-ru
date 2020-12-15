---
title: Интеллисенсехостфлагс | Документация Майкрософт
description: Перечисление Интеллисенсехостфлагс указывает флаги узла IntelliSense. В этой статье описываются значения перечисления.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b206cc4aa7c1ff388d6868fa8a0533d15da094ff
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487508"
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

|Члены|Описание|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Буфер контекста доступен только для чтения.|
|`IHF_NOSEPARATESUBJECT`|Нет текста темы. Буфер контекста содержит IntelliSense-Target (подразумевается `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Текст темы не поддерживает несколько строк.|
|`IHF_FORCECOMMITTOCONTEXT`|Эквивалентно `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|Редактирование (в теме или контексте) должно выполняться в режиме переввода.|

## <a name="requirements"></a>Требования
 Синглефилидитор. idl

## <a name="see-also"></a>См. также раздел
- <xref:Microsoft.VisualStudio.TextManager.Interop>
