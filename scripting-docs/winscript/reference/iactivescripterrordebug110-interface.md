---
title: Интерфейс IActiveScriptErrorDebug110 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 067a62ec8b87c448577cfd6e5789ae5e073b5fb8
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345907"
---
# <a name="iactivescripterrordebug110-interface"></a>IActiveScriptErrorDebug110 — интерфейс
Расширяет его функциональные возможности [интерфейс IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md). Этот интерфейс реализуется обработчиком JavaScript, чтобы определить, почему произошло событие BREAKREASON_ERROR.  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется в PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IActiveScriptErrorDebug110` предоставляет следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Возвращает вид исключения для созданного исключения.|