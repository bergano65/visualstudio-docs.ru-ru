---
title: Повышения производительности надстройки VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 918ff0ac0a0b7f4e16c779516c015d7b74cec415
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672656"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Повышения производительности надстройки VSTO
  Для повышения удобства работы пользователей можно оптимизировать надстройки VSTO, создаваемые для приложений Office, что позволит быстрее выполнять запуск, завершать работу, открывать элементы и выполнять другие задачи. Если ваша надстройка VSTO предназначена для Outlook, можно уменьшить вероятность ее отключения из-за низкой производительности. Для повышения производительности надстройки VSTO можно реализовать следующие стратегии:  
  
- [Загрузка надстроек VSTO по требованию](#Load).  
  
- [Публикация решений Office с помощью установщика Windows](#Publish).  
  
- [Обход отражения ленты](#Bypass).  
  
- [Выполнение ресурсоемких операций в отдельном потоке](#Perform).  
  
  Дополнительные сведения об оптимизации надстройки VSTO для Outlook см. в разделе [критерии производительности для сохранения VSTO Add-ins включен](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> Загрузка надстроек VSTO по требованию  
 Вы можете настроить надстройку VSTO так, чтобы она загружалась только при следующих обстоятельствах:  
  
- когда пользователь запускает приложение в первый раз после установки надстройки VSTO;  
  
- когда пользователь взаимодействует с надстройкой VSTO в первый раз после запуска приложения в любое другое последующее время.  
  
  Например, Ваша надстройка VSTO может вносить в лист с данными, когда пользователь нажимает кнопку, отмеченная как **получить мои данные**. Приложение должно загрузить Ваша надстройка VSTO по крайней мере один раз, чтобы **получить мои данные** появилась кнопка на ленте. Тем не менее надстройка VSTO не будет загружена снова когда пользователь запустит приложение в следующий раз. Надстройка VSTO загружается только в том случае, когда пользователь нажмет кнопку **Получить мои данные** .  
  
### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Настройка решения ClickOnce для загрузки надстроек VSTO по требованию  
  
1.  В области **Обозреватель решений**выберите узел проекта.  
  
2.  В строке меню выберите **Вид** > **Страницы свойств**.  
  
3.  На вкладке **Публикация** нажмите кнопку **Параметры** .  
  
4.  В диалоговом окне **Параметры публикации** выберите элемент списка **Параметры Office** , выберите параметр **Загружать по требованию** , а затем нажмите кнопку **ОК** .  
  
### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Настройка решения установщика Windows для загрузки надстроек VSTO по требованию  
  
1.  В реестре, задайте `LoadBehavior` запись **_корневой_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _Идентификатор надстройки_** ключа **0x10**.  
  
     Дополнительные сведения см. в разделе [записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Настройка решения для загрузки надстроек VSTO по требованию при отладке решения  
  
1.  Создайте сценарий, который задает `LoadBehavior` запись **_корневой_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _Идентификатор надстройки_** ключа **0x10**.  
  
     В следующем коде показан пример такого скрипта.  
  
    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]  
    "Description"="MyAddIn"  
    "FriendlyName"="MyAddIn"  
    "LoadBehavior"=dword:00000010  
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Создайте событие после сборки, которое обновляет реестр с помощью скрипта.  
  
     Ниже приведен пример командной строки, который можно добавить в событие после сборки.  
  
    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Сведения о создании события после сборки в C# проектов, см. в разделе [как: Укажите события построения &#40;C&#35;&#41;](/visualstudio/ide/how-to-specify-build-events-csharp).  
  
     Сведения о создании события после сборки в проекте Visual Basic, см. в разделе [как: Укажите события построения &#40;Visual Basic&#41;](/visualstudio/ide/how-to-specify-build-events-visual-basic).  
  
##  <a name="Publish"></a> Публикация решений Office с помощью установщика Windows  
 При публикации решения с помощью установщика Windows, Visual Studio 2010 Tools для Office runtime пропускает следующие действия, при загрузке надстройки VSTO.  
  
- Проверка схемы манифеста.  
  
- Автоматическая проверка наличия обновлений.  
  
- Проверка цифровых подписей манифестов развертывания.  
  
  > [!NOTE]  
  >  Такой подход не является обязательным, если вы развертываете Ваша надстройка VSTO надежное расположение на компьютере.  
  
  Дополнительные сведения см. в разделе [развертывание решения Office с помощью установщика Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Обход отражения ленты  
 При создании решения с помощью [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], убедитесь, что ваши пользователи установили самую последнюю версию Visual Studio 2010 Tools для Office runtime, при развертывании решения. Более старые версии среды выполнения выполняют отражение в сборки решения для поиска настроек ленты. Этот процесс может привести к замедлению загрузки надстройки VSTO.  
  
 Кроме того можно предотвратить использование отражения для определения настроек ленты любой версии Visual Studio 2010 Tools для Office runtime. Для применения такой стратегии Переопределите `CreateRibbonExtensibility` метод и явным образом возвращайте объекты ленты. Если Ваша надстройка VSTO не содержит никаких настроек ленты, возвращают `null` внутри метода.  
  
 В следующем примере возвращается объекта ленты выполняется на основе значения поля.  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
##  <a name="Perform"></a> Выполнение ресурсоемких операций в отдельном потоке  
 Рассмотрите возможность выполнения длительных задач (например, соединений с базой данных или других видов сетевых вызовов) в отдельном потоке. Дополнительные сведения см. в разделе [поддержка потоков в Office](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Весь код, вызывающий объектную модель Office, должен выполняться в основном потоке.  
  
## <a name="see-also"></a>См. также  
 [Загрузка по требованию VSTO Add-ins](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)   
 [Отложенная загрузка среды CLR в надстройках Office](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)   
 [Создание надстроек VSTO для Office с помощью Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)   
