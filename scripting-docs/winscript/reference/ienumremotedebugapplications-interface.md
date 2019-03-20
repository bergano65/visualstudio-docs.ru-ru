---
title: Интерфейс IEnumRemoteDebugApplications | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumRemoteDebugApplications interface
ms.assetid: ceb5fbe7-d131-4352-9dd1-af80acd3f3f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 430551002bc7603d86f9c7fb624ec438734bd766
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150625"
---
# <a name="ienumremotedebugapplications-interface"></a>Интерфейс IEnumRemoteDebugApplications
Перечисляет объекты приложения. Этот интерфейс можно использовать для перечисления запущенные приложения на компьютере для в диалоговом окне «Присоединение к приложению».  
  
 Помимо методов, наследуемых от `IUnknown`, `IEnumRemoteDebugApplications` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IEnumRemoteDebugApplications::Clone](../../winscript/reference/ienumremotedebugapplications-clone.md)|Создает перечислитель с тем же состоянием, что и текущий перечислитель.|  
|[IEnumRemoteDebugApplications::Next](../../winscript/reference/ienumremotedebugapplications-next.md)|Возвращает указанное количество сегментов в последовательности перечисления.|  
|[IEnumRemoteDebugApplications::Reset](../../winscript/reference/ienumremotedebugapplications-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[IEnumRemoteDebugApplications::Skip](../../winscript/reference/ienumremotedebugapplications-skip.md)|Пропускает заданное число сегментов в последовательности перечисления.|