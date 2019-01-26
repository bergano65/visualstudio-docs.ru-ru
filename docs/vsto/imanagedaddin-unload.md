---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 68ef36185c193263db386a1e1f80877c0327440c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874345"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Вызывается непосредственно перед выгрузкой управляемой надстройки VSTO.  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли завершен метод.  
  
## <a name="remarks"></a>Примечания  
 Этот метод не вызывается текущими версиями Microsoft Office. Этот метод зарезервирован для использования в будущем.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
