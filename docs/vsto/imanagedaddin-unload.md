---
title: IManagedAddin::Unload
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: db805aa1e00d672b4a0579e546a6827e9135b909
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673968"
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
  
  