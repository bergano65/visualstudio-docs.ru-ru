---
title: Пошаговое руководство. Загрузка сборок по требованию с помощью API развертывания ClickOnce с помощью конструктора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a7ff4fe24720f707c8f3faa330f71a8abda3c698
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686337"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Пошаговое руководство. Загрузка сборок по требованию с помощью API развертывания ClickOnce с помощью конструктора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

По умолчанию все сборки, включенные в приложение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , загружаются при первом его запуске. Однако некоторые части приложения могут быть нужны лишь небольшому числу пользователей. В этом случае рекомендуется скачивать сборку только при создании одного из ее типов. В следующем примере показано, как пометить определенные сборки в приложении как "необязательные" и скачивать их с помощью классов в пространстве имен <xref:System.Deployment.Application> , когда среда CLR нуждается в них.  
  
> [!NOTE]
> Для выполнения данной процедуры приложение должно выполняться с полным доверием.  
  
> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-projects"></a>Создание проектов  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Создание проекта, использующего сборку по запросу с помощью Visual Studio  
  
1. Создайте проект Windows Forms в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. В меню **Файл** выберите команду **Добавить**, а затем **Создать проект**. Выберите проект **Библиотека классов** в диалоговом окне и назовите его `ClickOnceLibrary`.  
  
    > [!NOTE]
    > В Visual Basic мы рекомендуем изменить свойства проекта, чтобы сменить корневое пространство имен для этого проекта на `Microsoft.Samples.ClickOnceOnDemand` или то, которое подходит вам. Для простоты два проекта в этом пошаговом руководстве находятся в одном пространстве имен.  
  
2. Определите класс `DynamicClass` с одним свойством `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
3. Выберите проект Windows Forms в **обозревателе решений**. Добавьте ссылку на сборку <xref:System.Deployment.Application> и ссылку на проект `ClickOnceLibrary` .  
  
    > [!NOTE]
    > В Visual Basic мы рекомендуем изменить свойства проекта, чтобы сменить корневое пространство имен для этого проекта на `Microsoft.Samples.ClickOnceOnDemand` или то, которое подходит вам. Для простоты два проекта в этом пошаговом руководстве находятся в одном пространстве имен.  
  
4. Щелкните форму правой кнопкой мыши, выберите **Просмотреть код** и добавьте следующие ссылки на форму.  
  
     [!code-csharp[ClickOnceOnDemand#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemand#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#1)]  
  
5. Добавьте следующий код для скачивания этой сборки по запросу. Этот код показывает, как сопоставить набор сборок с именем группы с помощью универсального класса <xref:System.Collections.DictionaryBase.Dictionary%2A> . Поскольку в этом пошаговом руководстве мы скачиваем только одну сборку, в нашей группе присутствует только одна сборка. В реальном приложении рекомендуется скачать сразу все сборки, связанные с одной функцией в приложении. Таблица сопоставлений позволяет легко сделать это, связав все библиотеки DLL, относящиеся к некоторому компоненту, с именем группы скачивания.  
  
     [!code-csharp[ClickOnceOnDemand#2](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#2)]
     [!code-vb[ClickOnceOnDemand#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#2)]  
  
6. В меню **Вид** выберите пункт **Панель элементов**. Перетащите <xref:System.Windows.Forms.Button> с **панели элементов** в форму. Дважды нажмите кнопку и добавьте приведенный ниже код в обработчик событий <xref:System.Windows.Forms.Control.Click> .  
  
     [!code-csharp[ClickOnceOnDemand#3](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#3)]
     [!code-vb[ClickOnceOnDemand#3](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#3)]  
  
## <a name="marking-assemblies-as-optional"></a>Пометка сборок как необязательных  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Пометка сборок как необязательных в приложении ClickOnce с помощью Visual Studio  
  
1. Щелкните правой кнопкой мыши проект Windows Forms в **обозревателе решений** и выберите пункт **Свойства**. Перейдите на вкладку **Публикация** .  
  
2. Нажмите кнопку **Файлы приложения** .  
  
3. Найдите описание для ClickOnceLibrary.dll. Задайте в раскрывающемся списке **Состояние публикации** значение **Включить**.  
  
4. Разверните раскрывающийся список **Группа** и выберите **Создать**. Введите имя `ClickOnceLibrary` в качестве имени новой группы.  
  
5. Продолжите публиковать приложение, как описано в разделе [как: опубликовать приложение ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Пометка сборок как необязательных в приложении ClickOnce с помощью Инструмента создания и изменения манифестов с графическим клиентом (MageUI.exe)  
  
1. Создание вашей [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифесты, как описано в разделе [Пошаговое руководство: Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2. Перед закрытием MageUI.exe выберите вкладку, содержащую манифест приложения развертывания и откройте на ней вкладку **Файлы** .  
  
3. Найдите ClickOnceLibrary.dll в списке файлов приложения и задайте в столбце **Тип файла** значение **Нет**. Для столбца **Группа** введите значение `ClickOnceLibrary.dll`.  
  
## <a name="testing-the-new-assembly"></a>Тестирование новой сборки  
  
#### <a name="to-test-your-on-demand-assembly"></a>Тестирование сборки по запросу  
  
1. Запустите приложение, развернутое с использованием [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2. Когда появится основная форма, нажмите <xref:System.Windows.Forms.Button>. В окне сообщения вы должны видеть строку "Hello, World!"  
  
## <a name="see-also"></a>См. также  
 <xref:System.Deployment.Application.ApplicationDeployment>
