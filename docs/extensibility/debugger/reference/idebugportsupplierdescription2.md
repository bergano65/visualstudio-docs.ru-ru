---
title: IDebugPortSupplierDescription2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3db59d4938911d0c47f0122a8727be8f1c8acd67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840201"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Позволяет [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательскому интерфейсу отображать текст в разделе **сведения о транспортировке** диалогового окна **Присоединение к процессу** .

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиками портов.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugPortSupplierDescription2` .

|Метод|Описание|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Извлекает метаданные описания и описания для поставщика порта.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
