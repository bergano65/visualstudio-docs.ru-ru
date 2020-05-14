---
title: IDebugGenericFieldОпределение (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 019633b62d46f6a8ac68e6f5f4abc888e6986ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728191"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Представляет определение поля для общего типа управляемого кода.

## <a name="syntax"></a>Синтаксис

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Строит экземпляр поля с учетом массива аргументов типа.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Извлекает параметры типа с учетом количества параметров.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Извлекает количество параметров типа, связанных с общим полем.|

## <a name="requirements"></a>Требования
 Заголовок: Sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
