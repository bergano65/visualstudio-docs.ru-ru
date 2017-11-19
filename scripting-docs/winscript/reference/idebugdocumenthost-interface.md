---
title: "Интерфейс IDebugDocumentHost | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adaeb98f18a052106036a91885696dd4b4760dea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthost-interface"></a>Интерфейс IDebugDocumentHost
Предоставляет функциональные возможности определенного узла, например цветовую подсветку синтаксиса, отладчик. `IDebugDocumentHelper::SetDebugDocumentHost` Метод принимает в качестве аргумента этот интерфейс.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugDocumentHost` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Возвращает диапазон символов, которые были добавлены с помощью `IDebugDocumentHelper::AddDeferredText`, в исходном документе узла.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Возвращает атрибуты текстового блока текста документа.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Уведомляет основное приложение, создается новый контекст документа и позволяет при необходимости возвращать объект, управляющий новый контекст узла.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Возвращает полный путь (включая имя файла) исходный файл документа.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Возвращает имя документа, без сведений о пути.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Уведомляет узел, что был сохранен файл исходного документа и обновить его содержимое.|