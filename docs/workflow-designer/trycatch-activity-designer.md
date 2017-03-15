---
title: "Конструктор действия &#171;TryCatch&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TryCatch.UI"
  - "System.Activities.Statements.Catch`1.UI"
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия &#171;TryCatch&#187;
Конструктор операций **TryCatch** используется для создания и настройки действия <xref:System.Activities.Statements.TryCatch>.  
  
## Действие TryCatch  
 Действие <xref:System.Activities.Statements.TryCatch> содержит действие <xref:System.Activities.Statements.TryCatch.Try%2A>, коллекцию действий **Catch\<TException\>** и действие <xref:System.Activities.Statements.TryCatch.Finally%2A>.Действие <xref:System.Activities.Statements.Catch%601> типа **TException** содержит <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> и <xref:System.Activities.Statements.Catch%601.Action%2A>.Оба они используются для реализации обработки типичных ошибок, основанной на исключении.Действие <xref:System.Activities.Statements.TryCatch> пытается выполнить свое действие <xref:System.Activities.Statements.TryCatch.Try%2A>.Если действие <xref:System.Activities.Statements.TryCatch.Try%2A> создает исключение, действие <xref:System.Activities.Statements.TryCatch> использует свою коллекцию **Catch\<TException\>** для сопоставления исключения.Если имеет место совпадение, то <xref:System.Activities.Statements.Catch%601.Action%2A> соответствующего **Catch\<TException\>** выполняется, что выполняет функцию логической обработки исключения.Если действия в разделах <xref:System.Activities.Statements.TryCatch.Try%2A> или <xref:System.Activities.Statements.TryCatch.Catches%2A> успешно выполняются, действие <xref:System.Activities.Statements.TryCatch> выполняет свое действие <xref:System.Activities.Statements.TryCatch.Finally%2A>.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Исключения](../Topic/Exceptions.md).  
  
### Использование конструктора действий TryCatch  
 Конструктор операций **TryCatch** можно найти в категории **Обработка ошибокОбласти элементов**, нажав на вкладку **Область элементов** по левую сторону [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Панель инструментов** из меню **Просмотр**, или же CTRL\+ALT\+X.\)  
  
 Конструктор операций **TryCatch** можно перетащить из **Области элементов** в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] в любое место, куда обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.TryCatch> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TryCatch.Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **TerminateWorkflow** либо в поле **DisplayName** таблицы свойств.Другие свойства необходимо изменить в области конструктора событий **TryCatch**.  
  
 Нажмите кнопку «развернуть» в правом вернем углу конструктора **TryCatch**, чтобы увидеть окна **Try**, **Catches** и **Finally** расширенном представлении.Чтобы добавить критерий обнаружения, нажмите кнопку «**Добавить новый критерий**» конструктора **TryCatch**.Кнопка преобразуется в поле со списком, в котором можно вводить текст.Выберите тип исключения и нажмите ВВОД, чтобы добавить критерий перехвата.После добавления **Catch**, область критерия перехвата развертывается и становится доступным действие, которое можно перетащить в эту область, чтобы выбрать логику выполнения для критерия перехвата.Обратите внимание на текстовое поле с правой стороны of развернутой области критериев.При помощи этого текстового поля можно назвать переменную исключения.Переменная исключения может использоваться только для действий внутри одного **Catch**.  
  
 Конструктор **TryCatch** не поддерживает изменение **Catch**.Если требуется изменить тип исключения, необходимо удалить **Catch** и добавить новый.**Catch** можно удалить, выбрав его или использовав меню **Удалить** в контекстном меню, доступ к которому можно получить правым щелчком.  
  
### Свойства TryCatch  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.TryCatch> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Указывает дополнительное понятное имя действия <xref:System.Activities.Statements.TryCatch>.Значение по умолчанию: TryCatch.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Действие, выполняемое первым при выполнении действия <xref:System.Activities.Statements.TryCatch>.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Коллекция элементов **Catch**, которые проверяются, когда действие <xref:System.Activities.Statements.TryCatch.Try%2A> вызывает исключение.<br /><br /> Требуется добавить по крайней мере одно действие в блок <xref:System.Activities.Statements.TryCatch.Catches%2A> или в блок <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Действие, которое необходимо выполнить, когда завершится выполнение <xref:System.Activities.Statements.TryCatch.Try%2A> и любых необходимых действий в коллекции <xref:System.Activities.Statements.TryCatch.Catches%2A>.<br /><br /> Требуется добавить по крайней мере одно действие в блок <xref:System.Activities.Statements.TryCatch.Catches%2A> или в блок <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
  
## См. также  
 [Коллекция](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)