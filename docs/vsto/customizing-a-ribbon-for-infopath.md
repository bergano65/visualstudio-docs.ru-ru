---
title: Настройка ленты для InfoPath | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3e5121285f66059a898ce64fc4107903f371485
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-a-ribbon-for-infopath"></a>Настройка ленты для InfoPath
  При настройке ленты в Microsoft Office InfoPath необходимо знать, где в приложении отображается пользовательская лента. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] может отображать ленту в окнах приложения InfoPath следующих трех типов.  
  
-   Окна, отображающие шаблон формы, открытый в режиме конструктора.  
  
-   Окна, отображающие форму, созданную на основе шаблона формы.  
  
-   Окно предварительного просмотра перед печатью.  
  
 **Применимость.** Информация в этой статье относится к проектам надстроек VSTO для InfoPath 2010. Дополнительные сведения см. в разделе [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Пользователи и разработчики открывают шаблон формы в режиме конструктора, чтобы изменить внешний вид и макет шаблона. Пользователи открывают формы, созданные на основе шаблона формы, для добавления содержимого.  
  
 Окно предварительного просмотра перед печатью позволяет разработчикам и пользователям просмотреть страницы формы или шаблона формы на экране перед тем, как отправить их на печать.  
  
> [!NOTE]  
>  Вкладка **Надстройки** не отображается в окне предварительного просмотра перед печатью. Если вы хотите, чтобы пользовательская вкладка отображалась в окне предварительного просмотра, убедитесь, что для свойства **OfficeId** вкладки не задано значение **TabAddIns**.  
  
 Необходимо указать тип ленты для каждого окна, в котором лента должна отображаться.  
  
## <a name="specifying-the-ribbon-type-in-the-ribbon-designer"></a>Указание типа ленты в конструкторе ленты  
 Если вы используете элемент **Лента (визуальный конструктор)** , щелкните свойство **RibbonType** ленты в окне **Свойства** и выберите один из идентификаторов ленты, описанных в следующей таблице.  
  
|Идентификатор ленты|Окно, в котором будет отображаться лента при выполнении проекта|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Окна, отображающие шаблон формы, открытый в режиме конструктора.|  
|**Microsoft.InfoPath.Editor**|Окна, отображающие форму, созданную на основе шаблона формы.|  
|**Microsoft.InfoPath.PrintPreview**|Окно предварительного просмотра перед печатью.|  
  
 В проект можно добавить несколько лент. Если несколько лент имеют одинаковый идентификатор, переопределите метод CreateRibbonExtensibilityObject в `ThisAddin` класс проекта, чтобы указать, какую ленту следует отображать во время выполнения. Дополнительные сведения см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Указание типа ленты с помощью XML-кода ленты  
 Если вы используете элемент **Лента (XML)** , проверьте значение параметра *ribbonID* в методе <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> и верните нужную ленту.  
  
 Метод <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> автоматически создается средой Visual Studio в файле кода ленты. Параметр *ribbonID* представляет собой строку, определяющую тип открываемого окна InfoPath.  
  
 В следующем примере кода показано, как отобразить пользовательскую ленту только в том окне, которое отображает шаблон формы в режиме конструктора. Отображаемая лента указывается в методе `GetResourceText()` , который создается в классе ленты. Дополнительные сведения о классе Ribbon см. в разделе [Ribbon XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>См. также  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [XML-ленты](../vsto/ribbon-xml.md)  
  
  