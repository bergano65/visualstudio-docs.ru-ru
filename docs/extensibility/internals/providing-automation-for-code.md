---
title: Предоставление автоматизации для кода | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3922de57a275dd24ce3161209b7775db104afada
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896439"
---
# <a name="providing-automation-for-code"></a>Предоставление автоматизации для кода
Создание модели автоматизации для кода не требуется. Пакет SDK для среды не предоставляет для этого образца. Сведения о модели кода, см. в разделе <xref:EnvDTE.CodeModel> объекта.  
  
 Чтобы реализовать модель кода, необходимо реализовать интерфейсы, которые определяются структуры внутренних данных. Объект, который должен быть производным от `IDispatch` класса.  
  
 Объекты, которые расширяют возможности, <xref:EnvDTE.CodeModel> и <xref:EnvDTE.FileCodeModel>, доступны из <xref:EnvDTE.Project> объекта и выглядеть следующим образом:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Можно выбрать для реализации только что `CodeModel` или `FileCodeModel` интерфейса в объекте, после возврата из вашей `Project` и <xref:EnvDTE.ProjectItem> объектов. Обеспечить функциональные возможности из этого интерфейса, который подходит для вашей системы проекта.  
  
 Если вы хотите добавить функции, такие как методы или свойства, которые недоступны из стандарта `CodeModel` и `FileCodeModel` интерфейсы, создайте собственный интерфейс, который наследует от стандартного. Убедитесь, что документ с вашей системой проекта, чтобы конечные пользователи будут искать его. Возвращает стандартный интерфейс, но пользователь может вызвать `QueryInterface` метода или приведение в интерфейс, если известно, что существует.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)