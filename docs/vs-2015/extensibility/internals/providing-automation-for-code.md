---
title: Предоставление автоматизации для кода | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d70958f88bcd48ce3e2a18f2b086367800541a22
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172879"
---
# <a name="providing-automation-for-code"></a>Предоставление автоматизации для кода
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Создание модели автоматизации для кода не требуется. Пакет SDK для среды не предоставляет для этого образца. Сведения о модели кода, см. в разделе <xref:EnvDTE.CodeModel> объекта.  
  
 Чтобы реализовать модель кода, необходимо реализовать интерфейсы, которые определяются структуры внутренних данных. Объект, который должен быть производным от `IDispatch` класса.  
  
 Объекты, которые расширяют возможности, <xref:EnvDTE.CodeModel> и <xref:EnvDTE.FileCodeModel>, доступны из <xref:EnvDTE.Project> объекта и выглядеть следующим образом:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Можно выбрать для реализации только что `CodeModel` или `FileCodeModel` интерфейса в объекте, после возврата из вашей `Project` и <xref:EnvDTE.ProjectItem> объектов. Обеспечить функциональные возможности из этого интерфейса, который подходит для вашей системы проекта.  
  
 Если вы хотите добавить функции, такие как методы или свойства, которые недоступны из стандарта `CodeModel` и `FileCodeModel` интерфейсы, создайте собственный интерфейс, который наследует от стандартного. Убедитесь, что документ с вашей системой проекта, чтобы конечные пользователи будут искать его. Возвращает стандартный интерфейс, но пользователь может вызвать `QueryInterface` метода или приведение в интерфейс, если известно, что существует.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)

