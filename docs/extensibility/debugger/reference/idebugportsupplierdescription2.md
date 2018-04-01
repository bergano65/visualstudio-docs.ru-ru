---
title: IDebugPortSupplierDescription2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d4fe70f9d0ef5273f30f16e99524247a2e45843c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Извлекает описание и описание метаданных для поставщика порта.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll