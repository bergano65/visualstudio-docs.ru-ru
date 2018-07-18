---
title: IDebugPortSupplierDescription2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c15facb38037272dcf2cef4f06d84d835b874012
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112839"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Включает [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательский Интерфейс для отображения текста внутри **сведения о транспорте** раздел **присоединиться к процессу** диалоговое окно.  
  
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
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Извлекает описание и описание метаданных для поставщика порта.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll