---
title: Интерфейс IDebugApplicationNode100 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8de6f57cabe808df1506870fe65da31ef74e644
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436036"
---
# <a name="idebugapplicationnode100-interface"></a>IDebugApplicationNode100 — интерфейс
`IDebugApplicationNode100` Интерфейс расширяет функциональные возможности [интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md). Экземпляр этого интерфейса можно получить путем вызова QueryInterface для реализации [интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
> Этот интерфейс реализуется в PDM v10.0 и больше. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IDebugApplicationNode100` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Получает текстовые документы, которые скрыты с помощью указанного фильтра.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Определяет, относится ли указанный документ на один из дочерних узлов данного узла.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Задает фильтр для конкретного [интерфейс IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) реализации. Она позволяет отладчиках скриптов отфильтровать компилятором дочерние узлы приложения таким образом, чтобы PDM больше не будет отправлять события при создании или удалить узлы. По умолчанию будут отправляться все узлы.|