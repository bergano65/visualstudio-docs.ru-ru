---
title: Источник функции управления пакета VSPackage | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93c2da699e0b40152442d38c4510e2a8c8ed5b54
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562926"
---
# <a name="source-control-vspackage-features"></a>Функции пакета VSPackage системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функции пакета VSPackage системы управления версиями](https://docs.microsoft.com/visualstudio/extensibility/internals/source-control-vspackage-features).  
  
В этом разделе описываются различные функции из пакета VSPackage системы управления версиями. Здесь указаны регистрации и выбора, подробные данные об таких VSPackage, а также рассматриваются три функций управления, связанных с основным источником: обработка событий запроса сохранить изменения запроса (QEQS), замену глифов и настраиваемый пользовательский интерфейс (UI) для системы управления версиями функции.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Регистрация и выбор](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)  
 Описываются механизмы регистрации и выбора пакета.  
  
 [Изменение запроса / сохранение запроса](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)  
 Поясняется в запрос изменения запроса сохранения событий и как они обрабатываются элементом управления источником VSPackage.  
  
 [Управление глифами](../../extensibility/internals/glyph-control-source-control-vspackage.md)  
 Описание уровней управления глифа и способы их реализации.  
  
 [Настраиваемый пользовательский](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)  
 Описываются элементы пользовательского интерфейса, которые можно указать пакет VSPackage системы управления версиями.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Описывает, как создать пакет VSPackage, который не только предоставляет функции системы управления версиями, но можно использовать для настройки системы управления версиями [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] система управления версиями пользовательского интерфейса.

