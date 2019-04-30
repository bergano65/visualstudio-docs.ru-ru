---
title: IDebugPortSupplierDescription2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5f210d3f0f8f2a9d28abee3d1956a3b4d09038a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918126"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Позволяет [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса для отображения текста внутри **сведения о транспорте** раздел **присоединение к процессу** диалоговое окно.

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщикам портов.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugPortSupplierDescription2`.

|Метод|Описание|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Извлекает описания и описание метаданных поставщика порта.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll