---
title: Интерфейс IDebugApplicationNode | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9be864fdb9468668633322066bbbcf11569e4eb3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147908"
---
# <a name="idebugapplicationnode-interface"></a>Интерфейс IDebugApplicationNode
`IDebugApplicationNode` Интерфейс расширяет функциональные возможности `IDebugDocumentProvider` интерфейс благодаря наличию контекста, в дереве проекта.  
  
 Помимо методов, наследуемых от `IDebugDocumentProvider`, `IDebugApplicationNode` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Перечисляет дочерние узлы данного узла приложения.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Возвращает родительский узел данного узла приложения.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Задает поставщик документа для данного узла приложения.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Вызывает это приложение освободить все ссылки и введите в неактивном состоянии.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Добавляет этот узел приложения в дерево указанный проект.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Удаляет данный узел приложения в дереве проекта.|