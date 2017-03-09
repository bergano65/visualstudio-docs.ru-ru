---
title: "Пошаговое руководство: вызов Visual Studio SDK с помощью автоматизации | Microsoft Docs"
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
  - "пошаговые руководства [Visual Studio SDK], вызов с помощью автоматизации"
ms.assetid: ca4dab48-632c-4c2a-8c84-57c027e37987
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Пошаговое руководство: вызов Visual Studio SDK с помощью автоматизации
В этом пошаговом руководстве показано, как создать надстройку Visual Studio, которая использует службу Visual Studio. Созданная надстройка получает поставщика службы и использует его для получения службы. Вы можете использовать ту же технику для получения любой предложенной службы Visual Studio. Дополнительные сведения о службах и поставщиках служб см. в разделе [Использование и предоставления услуг](../extensibility/using-and-providing-services.md). В процедурах ниже показано, как создать надстройку и получить службу из нее.  
  
## Создание надстройки  
 В этом разделе вы создадите надстройку Visual Studio с помощью шаблона проекта надстройки Visual Studio.  
  
#### Создание надстройки  
  
1.  Создайте новый проект Visual Studio \(**Файл\/Создать\/Проект**\).  
  
2.  В левой области диалогового окна **Новый проект** разверните узел **Другие типы проектов** и щелкните узел **Расширяемость**. Выберите **Надстройка Visual Studio**.  
  
3.  Создайте новый проект надстройки с именем `Addin`.  
  
     В мастере надстроек [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] нажмите кнопку **Далее**.  
  
4.  На странице **Выбрать язык программирования** щелкните **Создать надстройки, используя Visual C\#** или **Создать надстройки, используя Visual Basic**.  
  
5.  На странице **Выбор узла приложения** щелкните **Microsoft Visual Studio \<версия\>**.  
  
6.  На странице **Ввод имени и описания** введите `MyAddin` в поле **Имя** и `MyAddin Walkthrough` в поле **Описание**.  
  
7.  На странице **Выбор параметров надстройки** установите флажок для элемента меню "Сервис" в разделе **Создать интерфейс панели команд для надстройки?**. Снимите остальные флажки.  
  
8.  Примите все остальные значения по умолчанию.  
  
9. Выполните сборку решения и убедитесь в том, что оно компилируется без ошибок.  
  
## Получение службы из надстройки  
 Следующие шаги описывают приобретение службы из надстройки.  
  
#### Получение службы  
  
1.  Откройте файл Connect.cs или Connect.vb и добавьте эти строки к операторам `using` \(C\#\) или `Imports` \(Visual Basic\):  
  
     [!CODE [VSSDKAddin#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkaddin#1)]  
  
2.  Щелкните правой кнопкой мыши узел проекта в **Обозревателе решений** и добавьте следующие ссылки .NET:  
  
    ```  
    Microsoft.VisualStudio.OLE.Interop Microsoft.VisualStudio.Shell.Interop  
    ```  
  
3.  Добавьте эти строки кода к предложению `if(commandName == "Addin.Connect.Addin")` или `If commandName = "Addin.Connect.Addin" Then` метода `Exec`:  
  
     [!CODE [VSSDKAddin#2](../CodeSnippet/VS_Snippets_VSSDK/vssdkaddin#2)]  
  
     Этот код приводит текущий объект приложения \(тип `DTE2`\) к `IOleServiceProvider`, а затем вызывает `QueryService` для получения службы <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>. Эта служба предоставляет интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> отображает окно сообщения при запуске надстройки.  
  
4.  Выполните сборку проекта надстройки в режиме отладки, нажав клавишу F5.  
  
     Запустится другой экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
5.  В новом экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в меню **Сервис** щелкните **Надстройка**. В окне сообщений отобразится следующее:  
  
    ```  
    MyAddin Inside Addin.Connect  
    ```  
  
## См. также  
 [Практическое руководство. Отключение и удаление надстройки](../Topic/How%20to:%20Deactivate%20and%20Remove%20an%20Add-In.md)