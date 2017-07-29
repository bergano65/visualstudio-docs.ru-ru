---
title: "Практическое руководство. Создание шаблонов проектов | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 279a123088308a54dccfa9abe0bfbcdb18e5aaf1
ms.contentlocale: ru-ru
ms.lasthandoff: 05/31/2017

---
# <a name="how-to-create-project-templates"></a>Практическое руководство. Создание шаблонов проектов
Эта процедура позволяет создать шаблон с помощью мастера **экспорта шаблонов**, который упаковывает шаблон в ZIP-файл. Вы можете создать шаблоны в формате VSI для более эффективного развертывания с помощью расширения мастера экспорта шаблонов или с помощью шаблонов, включенных в [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]. Кроме того, шаблоны можно создавать вручную.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Создание настраиваемого шаблона проекта с помощью стандартного мастера экспорта шаблонов  
  
1.  Создайте проект.  
  
    > [!NOTE]
    >  Называя проект, который будет источником для шаблонов, используйте только допустимые символы идентификаторов. Шаблон, экспортированный из проекта, имя которого содержит недопустимые символы, может привести к ошибкам компиляции в будущих проектах, основанных на шаблоне. Дополнительные сведения о допустимых символах идентификаторов см. в статье [Имена объявленных элементов](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
2.  Внесите в проект все необходимые изменения, пока он не будет готов к сохранению в качестве шаблона.  
  
3.  По мере необходимости отредактируйте файл кода, чтобы указать, где должна быть выполнена замена параметра. Дополнительные сведения о замене параметров см. в разделе [Практическое руководство. Замена параметров в шаблоне](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  В меню **Проект** выберите команду **Экспорт шаблона**. Откроется мастер **экспорта шаблонов**.  
  
5.  Щелкните **Шаблон проекта**.  
  
6.  При наличии нескольких проектов в текущем решении выберите проекты, которые требуется экспортировать в шаблон.  
  
7.  Нажмите кнопку **Далее**.  
  
8.  Выберите значок и рисунок предварительного просмотра для создаваемого шаблона. Они будут отображаться в диалоговом окне **Новый проект**.  
  
9. Введите имя и описание шаблона.  
  
10. Нажмите кнопку **Готово**. Проект будет экспортирован в ZIP-файл и помещен в указанное расположение вывода, а также (если установлен соответствующий флажок) импортирован в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Если у вас установлен [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)], можно поместить готовый шаблон в оболочку — VSIX-файл для развертывания с помощью шаблона **Проект VSIX**. Дополнительные сведения см. в разделе [Приступая к работе с использованием шаблона проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>См. также  
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Практическое руководство. Создание шаблонов элементов](../ide/how-to-create-item-templates.md)

