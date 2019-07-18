---
title: Интерфейс IActiveScriptErrorDebug110 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110 Interface
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72f545f5a48fc7b8aa3f9250b13a62ba659e94bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436058"
---
# <a name="iactivescripterrordebug110-interface"></a>IActiveScriptErrorDebug110 — интерфейс
Расширяет его функциональные возможности [интерфейс IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md). Этот интерфейс реализуется обработчиком JavaScript, чтобы определить, почему произошло событие BREAKREASON_ERROR.  
  
> [!IMPORTANT]
> Этот интерфейс реализуется в PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IActiveScriptErrorDebug110` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Возвращает вид исключения для созданного исключения.|