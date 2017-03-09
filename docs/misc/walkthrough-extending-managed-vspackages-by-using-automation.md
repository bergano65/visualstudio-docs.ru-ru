---
title: "Пошаговое руководство. Расширение управляемых пакетов VSPackage с помощью автоматизации | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "управляемые пакеты VSPackage, расширение с помощью автоматизации"
  - "автоматизация [пакет SDK для Visual Studio], пошаговые руководства"
  - "автоматизация [пакет SDK для Visual Studio], управляемые пакеты VSPackage"
ms.assetid: 7fd2000b-8ec3-4d83-b169-d38008fb57ee
caps.latest.revision: 35
caps.handback.revision: 35
manager: "douge"
---
# Пошаговое руководство. Расширение управляемых пакетов VSPackage с помощью автоматизации
В этом пошаговом руководстве описывается создание управляемого пакета VSPackage, который управляет интегрированной средой разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], с помощью автоматизации. Вы создадите управляемый пакет VSPackage, а затем используете методы автоматизации в полученном пакете для отображения свойств [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в окне **выходных данных**.  
  
## Обязательные компоненты  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации см. [SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Расположения шаблона проекта пакета Visual Studio  
 Шаблон проекта пакета Visual Studio можно найти в трех разных местах диалогового окна **Создание проекта**.  
  
1.  В разделе Visual Basic, "Расширяемость". Язык проекта по умолчанию — Visual Basic.  
  
2.  В разделе Visual C\#, "Расширяемость". Язык проекта по умолчанию — C\#.  
  
3.  В разделе "Другие типы проектов", "Расширяемость". Язык проекта по умолчанию — C\+\+.  
  
### Создание управляемого пакета VSPackage  
  
1.  Создайте проект пакета [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с именем `Auto`.  
  
     Дополнительные сведения о создании управляемого пакета VSPackage см. в разделе [Пошаговое руководство. Создание команды меню с помощью шаблона пакета Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  На странице **Выбрать язык программирования** выберите язык [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
3.  На странице **Базовые сведения о пакете VSPackage** оставьте значения по умолчанию.  
  
4.  На странице **Выберите параметры пакета VSPackage** установите флажок **Команда меню**.  
  
5.  На странице **Параметры команды** измените значение параметра **Имя команды** на `Auto`.  
  
6.  Нажмите кнопку **Готово**.  
  
     Шаблон создаст управляемый проект с именем Auto.  
  
7.  Выполните сборку решения и убедитесь в том, что оно компилируется без ошибок.  
  
### Вызов модели автоматизации  
  
1.  В **обозревателе решений** щелкните правой кнопкой мыши узел проекта Auto и выберите пункт **Добавить** \> **Ссылка**.  
  
2.  На вкладке **.NET** диалогового окна **Ссылка** дважды щелкните элемент **EnvDTE**.  
  
     Будет добавлена ссылка на пространство имен автоматизации EnvDTE.  
  
3.  В файле AutoPackage добавьте указанную ниже ссылку на пространство имен.  
  
     [!code-cs[VSSDKAuto#1](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_1.cs)]
     [!code-vb[VSSDKAuto#1](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_1.vb)]  
  
4.  В файле AutoPackage замените тело метода `MenuItemCallback` на следующие строки:  
  
     [!code-cs[VSSDKAuto#2](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_2.cs)]
     [!code-vb[VSSDKAuto#2](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_2.vb)]  
  
 Этот код вызывает <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> для получения объекта автоматизации <xref:EnvDTE.DTE>, представляющего интегрированную среду разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Код автоматизации в `MenuItemCallback` создает новую область в окне **выходных данных** с именем **Test**. Затем имя и версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] записываются в новую область **выходных данных**.  
  
1.  Выполните сборку и запуск проекта Auto в режиме отладки, нажав клавишу F5.  
  
     При этом запустится экспериментальная сборка [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp\).  
  
    > [!NOTE]
    >  На этом этапе открыты обе версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp в меню **Сервис** выберите пункт **Авто**.  
  
     В окне **выходных данных** откроется новая область с именем **Test**, содержащая следующие данные:  
  
    ```  
    Name is Microsoft Visual Studio Version is x.xx  
    ```  
  
     Здесь x.xx — это номер последней версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Дополнительные примеры автоматизации см. на странице [Примеры автоматизации для Visual Studio](http://www.microsoft.com/downloads/details.aspx?familyid=3ff9c915-30e5-430e-95b3-621dccd25150&displaylang=en).  
  
## См. также  
 [Расширение среды Visual Studio](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)