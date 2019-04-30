---
title: Интерфейс IDebugDocumentHost | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 226e2700b471cd34496682d233e57946e124ff3b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939230"
---
# <a name="idebugdocumenthost-interface"></a>Интерфейс IDebugDocumentHost
Предоставляет функциональные возможности среды размещения, например раскраски синтаксиса, отладчику. `IDebugDocumentHelper::SetDebugDocumentHost` Метод принимает этот интерфейс в качестве аргумента.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugDocumentHost` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Возвращает диапазон символов, которые были добавлены с помощью `IDebugDocumentHelper::AddDeferredText`, в исходном документе узла.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Возвращает атрибуты текста для блока текста документа.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Уведомляет ведущее приложение, создается новый контекст документа и позволяет узлу, чтобы при необходимости вернуть объект, управляющий новый контекст.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Возвращает полный путь (включая имя файла) исходного файла документа.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Возвращает имя документа, без сведений о пути.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Уведомляет ведущее приложение, что был сохранен файл исходного документа, и что его содержимое должно обновляться.|