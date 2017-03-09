---
title: "Практическое руководство. Включение отладки для приложений ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "отладка веб-приложений ASP.NET"
  - "Файл конфигурации Web.config, режим отладки"
  - "отладка [Visual Studio], ASP.NET"
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Практическое руководство. Включение отладки для приложений ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Для включения отладки необходимо включить ее на странице **Свойства проекта** и в файле web.config приложения.  
  
> [!NOTE]  
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Включение отладки ASP.NET в свойствах проекта (Visual Basic/C#)  
  
1.  В окне **Обозреватель решений**правой кнопкой мыши щелкните имя веб-проекта и выберите пункт **Свойства**.  
  
2.  На странице свойств проекта перейдите на вкладку **Веб** .  
  
3.  В окне **Отладчики**установите флажок **ASP.NET** .  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Включение отладки в файле web.config  
  
1.  Откройте файл web.config с использованием любого стандартного текстового редактора или анализатора XML.  
  
    > [!NOTE]  
    > Удаленный доступ к этому файлу с помощью браузера невозможен. Из соображений безопасности настройка служб Microsoft IIS [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] осуществляется ASP.NET таким образом, чтобы предотвратить прямой доступ к файлам Web.config с помощью браузеров. При попытке доступа к файлу конфигурации с помощью браузера будет выдана ошибка доступа HTTP 403.  
  
2.  Файл Web.config — это XML-файл, поэтому он содержит вложенные разделы, помеченные тегами. Найдите элемент `configuration/system.web/compilation` . Если элемент compilation не существует, создайте его.  
  
3.  Если элемент `compilation` не содержит атрибут `debug` , добавьте этот атрибут к элементу.  
  
4.  Убедитесь в том, что значение атрибута `debug` равно `true`.  
  
Файл Web.config должен выглядеть, как следующий пример. Обратите внимание, что между элементами system.web и configuration могут быть другие разделы  
  
-   разделы элементов между элементами system.web и configuration  
  
-   разделы элементов между элементами system.web и compilation  
  
-   Элемент compilation может содержать другие элементы или атрибуты  
  
## <a name="example"></a>Пример  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Отказоустойчивость  
С помощью объекта [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] производится автоматическое обнаружение изменений в файлах Web.config и применяются новые параметры конфигурации. При этом нет необходимости перезагружать компьютер или IIS, чтобы изменения вступили в силу.  
  
Веб-сайт может содержать несколько виртуальных каталогов и подкаталогов. и файлы Web.config могут содержаться в каждом из них. Приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] наследуют параметры от файлов Web.config, находящихся на более высоких уровнях URL-пути. Файлы иерархической конфигурации позволяют изменять параметры различных приложений [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] одновременно, например, для всех приложений, расположенных ниже по иерархии. Однако если атрибут `debug` задан в файле, находящемся ниже по иерархии, то он будет переопределять более высокое значение.  
  
Например, можно указать значение `debug="true"` в файле, расположенном по адресу www.microsoft.com/aaa/Web.config, и любые приложения в папке aaa, а также любом подкаталоге aaa, будут наследовать эту настройку. Поэтому, если приложение [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] находится по адресу www.microsoft.com/aaa/bbb, то оно будет наследовать эту настройку, а также ее будут наследовать любые приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] из каталогов www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd и т. д. Единственное исключение — случай, когда одно из приложений переопределяет настройку посредством собственного файла Web.config, находящегося ниже по иерархии.  
  
Включение режима отладки сильно отразится на производительности приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . Режим отладки следует отключить перед развертыванием конечного приложения или перед оценкой его производительности.  
  
## <a name="see-also"></a>См. также  
[Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)  
  
