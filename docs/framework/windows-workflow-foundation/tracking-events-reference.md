---
title: Отслеживание ссылок на события
ms.date: 03/30/2017
ms.assetid: c1c1ee87-f80a-449b-acd0-50d81eef116e
ms.openlocfilehash: 5b3bba83b3c6c7ab27c9470213b7675f7e107c7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699881"
---
# <a name="tracking-events-reference"></a>Отслеживание ссылок на события
При выполнении рабочего процесса в [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] создаются события отслеживания при переходе его через различные этапы времени существования. Узел можно подписать на эти события, что позволит получать последние сведения о состоянии рабочего процесса на протяжении времени его существования. Создаваемые события отслеживания описываются в этом разделе.  
  
## <a name="event-reference"></a>Ссылка на событие  
  
|Идентификатор события|Уровень события|Сообщение о событии|Ключевые слова|  
|--------------|-----------------|-------------------|--------------|  
|[100 ― WorkflowInstanceRecord](100-workflowinstancerecord.md)|Сведения|TrackRecord=WorkflowInstanceRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, ActivityDefinitionId=%4, State=%5, Annotations=%6, ProfileName=%7|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[101 ― WorkflowInstanceUnhandledExceptionRecord](101-workflowinstanceunhandledexceptionrecord.md)|Error|TrackRecord=WorkflowInstanceUnhandledExceptionRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, ActivityDefinitionId=%4, SourceName=%5, SourceId=%6, SourceInstanceId=%7, SourceTypeName=%8, Exception=%9, Annotations=%10, ProfileName=%11|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[102 ― WorkflowInstanceAbortedRecord](102-workflowinstanceabortedrecord.md)|Предупреждение|TrackRecord=WorkflowInstanceAbortedRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, ActivityDefinitionId=%4, Reason=%5, Annotations=%6, ProfileName=%7|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[103 ― ActivityStateRecord](103-activitystaterecord.md)|Сведения|TrackRecord = ActivityStateRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, State = %4, Name=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Arguments=%9, Variables=%10, Annotations=%11, ProfileName = %12|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[104 ― ActivityScheduledRecord](104-activityscheduledrecord.md)|Сведения|TrackRecord=ActivityScheduledRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, Name =%4, ActivityId=%5, ActivityInstanceId=%6, ActivityTypeName=%7, ChildActivityName=%8, ChildActivityId=%9, ChildActivityInstanceId=%10, ChildActivityTypeName=%11, Annotations=%12, ProfileName=%13|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[105 ― FaultPropagationRecord](105-faultpropagationrecord.md)|Предупреждение|TrackRecord = FaultPropagationRecord, InstanceID=%1, RecordNumber=%2, EventTime=%3, FaultSourceActivityName=%4, FaultSourceActivityId=%5, FaultSourceActivityInstanceId=%6, FaultSourceActivityTypeName=%7, FaultHandlerActivityName=%8, FaultHandlerActivityId=%9, FaultHandlerActivityInstanceId=%10, FaultHandlerActivityTypeName=%11, Fault=%12, IsFaultSource=%13, Annotations=%14, ProfileName=%15|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[106 ― CancelRequestRecord](106-cancelrequestrecord.md)|Сведения|TrackRecord=CancelRequestedRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityId=%5, ActivityInstanceId=%6, ActivityTypeName=%7, ChildActivityName=%8, ChildActivityId=%9, ChildActivityInstanceId=%10, ChildActivityTypeName=%11, Annotations=%12, ProfileName=%13|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[107 ― BookmarkResumptionRecord](107-bookmarkresumptionrecord.md)|Сведения|TrackRecord=BookmarkResumptionRecord, InstanceId=%1, RecordNumber=%2,EventTime=%3, Name=%4, SubInstanceID=%5, OwnerActivityName=%6, OwnerActivityId=%7, OwnerActivityInstanceId=%8, OwnerActivityTypeName=%9, Annotations=%10, ProfileName=%11|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[108 ― CustomTrackingRecordInfo](108-customtrackingrecordinfo.md)|Сведения|TrackRecord=CustomTrackingRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName=%11|UserEvents, EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[110 ― CustomTrackingRecordWarning](110-customtrackingrecordwarning.md)|Предупреждение|TrackRecord=CustomTrackingRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName=%11|UserEvents, EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[111 — CustomTrackingRecordError](111-customtrackingrecorderror.md)|Error|TrackRecord=CustomTrackingRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName=%11|UserEvents, EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[112 ― WorkflowInstanceSuspendedRecord](112-workflowinstancesuspendedrecord.md)|Сведения|TrackRecord=WorkflowInstanceSuspendedRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, ActivityDefinitionId=%4, Reason=%5, Annotations=%6, ProfileName=%7|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[113 — WorkflowInstanceTerminatedRecord](113-workflowinstanceterminatedrecord.md)|Error|TrackRecord=WorkflowInstanceTerminatedRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, ActivityDefinitionId=%4, Reason=%5, Annotations=%6, ProfileName=%7|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|[114 — WorkflowInstanceRecordWithId](114-workflowinstancerecordwithid.md)|Сведения|TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|HealthMonitoring, WFTracking|  
|[115 — WorkflowInstanceAbortedRecordWithId](115-workflowinstanceabortedrecordwithid.md)|Предупреждение|TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|HealthMonitoring, WFTracking|  
|[116 ― WorkflowInstanceSuspendedRecordWithId](116-workflowinstancesuspendedrecordwithid.md)|Сведения|TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|HealthMonitoring, WFTracking|  
|[117 — WorkflowInstanceTerminatedRecordWithId](117-workflowinstanceterminatedrecordwithid.md)|Error|TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|HealthMonitoring, WFTracking|  
|[118 — WorkflowInstanceUnhandledExceptionRecordWithId](118-workflowinstanceunhandledexceptionrecordwithid.md)|Error|TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName = %8, Exception = %9, Annotations = % 10, ProfileName = % 11, WorkflowDefinitionIdentity = % 12|HealthMonitoring, WFTrackingHealthMonitoring, WFTracking|  
|[119 — WorkflowInstanceUpdatedRecord](119-workflowinstanceupdatedrecord.md)|Сведения|TrackRecord= WorkflowInstanceUpdatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, Annotations = %8, ProfileName = %9|HealthMonitoring, WFTracking|  
|[225 — TraceCorrelationKeys](225-tracecorrelationkeys.md)|Сведения|Вычисленный ключ корреляции «%1» с использованием значений «%2» в родительской области «%3».|Устранение неполадок для служб WFServices|  
|[440 — StartSignpostEvent1](440-startsignpostevent.md)|Сведения|Граница действия.|Устранение неполадок для служб WFServices|  
|[441 — StopSignpostEvent1](441-stopsignpostevent.md)|Сведения|Граница действия.|Устранение неполадок для служб WFServices|  
|[1001 — WorkflowApplicationCompleted](1001-workflowapplicationcompleted.md)|Сведения|Элемент WorkflowInstance с идентификатором «%1» завершил работу в состоянии Closed.|WFRuntime|  
|[1002 — WorkflowApplicationTerminated](1002-workflowapplicationterminated.md)|Сведения|WorkflowApplication с идентификатором «%1» остановлено. Был прерван в состоянии сбоя с исключением.|WFRuntime|  
|[1003 — WorkflowInstanceCanceled](1003-workflowinstancecanceled.md)|Сведения|Элемент WorkflowInstance с идентификатором «%1» завершил работу в состоянии Canceled.|WFRuntime|  
|[1004 — WorkflowInstanceAborted](1004-workflowinstanceaborted.md)|Сведения|Выполнение элемента WorkflowInstance с идентификатором «%1» было прервано в результате исключения.|WFRuntime|  
|[1005 — WorkflowApplicationIdled](1005-workflowapplicationidled.md)|Сведения|WorkflowApplication с идентификатором «%1» перешло в состояние простоя.|WFRuntime|  
|[1006 — WorkflowApplicationUnhandledException](1006-workflowapplicationunhandledexception.md)|Error|Элемент WorkflowInstance с идентификатором: «%1» обнаружил необработанное исключение.  Возникло исключение из действия «%2», DisplayName: «%3».  Будет предпринято следующее действие: %4.|WFRuntime|  
|[1007 — WorkflowApplicationPersisted](1007-workflowapplicationpersisted.md)|Сведения|Элемент WorkflowApplication с идентификатором «%1» сохранен.|WFRuntime|  
|[1008 — WorkflowApplicationUnloaded](1008-workflowapplicationunloaded.md)|Сведения|Элемент WorkflowInstance с идентификатором «%1» выгружен из памяти.|WFRuntime|  
|[1009 — ActivityScheduled](1009-activityscheduled.md)|Сведения|Родительское действие «%1» (отображаемое имя «%2», ИД экземпляра «%3») запланировало дочернее действие «%4» (отображаемое имя «%5», ИД экземпляра «%6»).|WFRuntime|  
|[1010 — ActivityCompleted](1010-activitycompleted.md)|Сведения|Родительское действие «%1» (отображаемое имя «%2», ИД экземпляра «%3») запланировало дочернее действие «%4» (отображаемое имя «%5», ИД экземпляра «%6»).|WFRuntime|  
|[1011 — ScheduleExecuteActivityWorkItem](1011-scheduleexecuteactivityworkitem.md)|Verbose|ExecuteActivityWorkItem запланирован для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1012 — StartExecuteActivityWorkItem](1012-startexecuteactivityworkitem.md)|Verbose|Начато выполнение ExecuteActivityWorkItem для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1013 — CompleteExecuteActivityWorkItem](1013-completeexecuteactivityworkitem.md)|Verbose|Завершено выполнение ExecuteActivityWorkItem для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1014 — ScheduleCompletionWorkItem](1014-schedulecompletionworkitem.md)|Verbose|CompletionWorkItem запланирован для родительского действия «%1», DisplayName: «%2», InstanceId: «%3».  Завершено действие «%4», DisplayName «%5», InstanceId «%6».|WFRuntime|  
|[1015 — StartCompletionWorkItem](1015-startcompletionworkitem.md)|Verbose|Начато выполнение CompletionWorkItem для родительского действия «%1», DisplayName «%2», InstanceId «%3». Завершено действие «%4», DisplayName «%5», InstanceId «%6».|WFRuntime|  
|[1016 — CompleteCompletionWorkItem](1016-completecompletionworkitem.md)|Verbose|CompletionWorkItem завершен для родительского действия «%1», DisplayName «%2», InstanceId «%3». Завершено действие «%4», DisplayName «%5», InstanceId «%6».|WFRuntime|  
|[1017 — ScheduleCancelActivityWorkItem](1017-schedulecancelactivityworkitem.md)|Verbose|CancelActivityWorkItem запланирован для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1018 — StartCancelActivityWorkItem](1018-startcancelactivityworkitem.md)|Verbose|Начато выполнение CancelActivityWorkItem для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1019 — CompleteCancelActivityWorkItem](1019-completecancelactivityworkitem.md)|Verbose|CancelActivityWorkItem завершен для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1020 — CreateBookmark](1020-createbookmark.md)|Verbose|Закладка будет создана для действия «%1», DisplayName: «%2», InstanceId: «%3».  BookmarkName: %4, BookmarkScope: %5.|WFRuntime|  
|[1021 — ScheduleBookmarkWorkItem](1021-schedulebookmarkworkitem.md)|Verbose|BookmarkWorkItem запланирован для действия «%1», DisplayName: «%2», InstanceId: «%3».  BookmarkName: %4, BookmarkScope: %5.|WFRuntime|  
|[1022 — StartBookmarkWorkItem](1022-startbookmarkworkitem.md)|Verbose|Начато выполнение BookmarkWorkItem для действия «%1», DisplayName: «%2», InstanceId: «%3».  BookmarkName: %4, BookmarkScope: %5.|WFRuntime|  
|[1023 — CompleteBookmarkWorkItem](1023-completebookmarkworkitem.md)|Verbose|BookmarkWorkItem завершен для действия «%1», DisplayName «%2», InstanceId «%3». BookmarkName: %4, BookmarkScope: %5.|WFRuntime|  
|[1024 — CreateBookmarkScope](1024-createbookmarkscope.md)|Verbose|Создан объект BookmarkScope: %1.|WFRuntime|  
|[1025 — BookmarkScopeInitialized](1025-bookmarkscopeinitialized.md)|Verbose|Объект BookmarkScope с идентификатором TemporaryId: «%1» инициализирован идентификатором «%2».|WFRuntime|  
|[1026 — ScheduleTransactionContextWorkItem](1026-scheduletransactioncontextworkitem.md)|Verbose|TransactionContextWorkItem запланирован для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1027 — StartTransactionContextWorkItem](1027-starttransactioncontextworkitem.md)|Verbose|Начато выполнение TransactionContextWorkItem для родительского действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1028 — CompleteTransactionContextWorkItem](1028-completetransactioncontextworkitem.md)|Verbose|TransactionContextWorkItem завершен для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1029 — ScheduleFaultWorkItem](1029-schedulefaultworkitem.md)|Verbose|FaultWorkItem запланирован для действия «%1», DisplayName: «%2», InstanceId: «%3».  Исключение распространено из действия «%4», DisplayName «%5», InstanceId «%6».|WFRuntime|  
|[1030 — StartFaultWorkItem](1030-startfaultworkitem.md)|Verbose|Начато выполнение FaultWorkItem для действия «%1», DisplayName: «%2», InstanceId: «%3».  Исключение распространено из действия «%4», DisplayName «%5», InstanceId «%6».|WFRuntime|  
|[1031 — CompleteFaultWorkItem](1031-completefaultworkitem.md)|Verbose|FaultWorkItem завершено для действия «%1», DisplayName «%2», InstanceId «%3». Исключение распространено из действия «%4», DisplayName «%5», InstanceId «%6».|WFRuntime|  
|[1032 — ScheduleRuntimeWorkItem](1032-scheduleruntimeworkitem.md)|Verbose|Рабочий элемент среды выполнения запланирован для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1033 — StartRuntimeWorkItem](1033-startruntimeworkitem.md)|Verbose|Начато выполнение рабочего элемента среды выполнения для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1034 — CompleteRuntimeWorkItem](1034-completeruntimeworkitem.md)|Verbose|Рабочий элемент среды выполнения завершен для действия «%1», DisplayName «%2», InstanceId «%3».|WFRuntime|  
|[1035 — RuntimeTransactionSet](1035-runtimetransactionset.md)|Verbose|Транзакция среды выполнения установлено с помощью действия «%1», DisplayName: «%2», InstanceId: «%3».  Выполнение изолированного действия «%4», DisplayName: «%5», InstanceId: «%6».|WFRuntime|  
|[1036 — RuntimeTransactionCompletionRequested](1036-runtimetransactioncompletionrequested.md)|Verbose|Действие «%1», DisplayName «%2», InstanceId «%3» запланировало завершение транзакции времени выполнения.|WFRuntime|  
|[1037 — RuntimeTransactionComplete](1037-runtimetransactioncomplete.md)|Verbose|Транзакция среды выполнения завершена с состоянием «%1».|WFRuntime|  
|[1038 — EnterNoPersistBlock](1038-enternopersistblock.md)|Verbose|Выполняется вход в непостоянный блок.|WFRuntime|  
|[1039 — ExitNoPersistBlock](1039-exitnopersistblock.md)|Verbose|Выполняется выход из непостоянного блока.|WFRuntime|  
|[1040 — InArgumentBound](1040-inargumentbound.md)|Verbose|В аргументе «%1» действия «%2», DisplayName «%3», InstanceId «%4» были связаны со значением %5.|WFActivities|  
|[1041 — WorkflowApplicationPersistableIdle](1041-workflowapplicationpersistableidle.md)|Сведения|WorkflowApplication с идентификатором: «%1» бездействует и сохраняемо.  Будет предпринято следующее действие: %2.|WFRuntime|  
|[1101 — WorkflowActivityStart](1101-workflowactivitystart.md)|Сведения|Элемент WorkflowInstance с идентификатором «%1», действие E2E|WFRuntime|  
|[1102 — WorkflowActivityStop](1102-workflowactivitystop.md)|Сведения|Элемент WorkflowInstance с идентификатором «%1», действие E2E|WFRuntime|  
|[1103 — WorkflowActivitySuspend](1103-workflowactivitysuspend.md)|Сведения|Элемент WorkflowInstance с идентификатором «%1», действие E2E|WFRuntime|  
|[1104 — WorkflowActivityResume](1104-workflowactivityresume.md)|Сведения|Элемент WorkflowInstance с идентификатором «%1», действие E2E|WFRuntime|  
|[1124 — InvokeMethodIsStatic](1124-invokemethodisstatic.md)|Сведения|Метод InvokeMethod «%1»: метод является статическим.|WFRuntime|  
|[1125 — InvokeMethodIsNotStatic](1125-invokemethodisnotstatic.md)|Сведения|Метод InvokeMethod «%1»: метод не является статическим.|WFRuntime|  
|[1126 — InvokedMethodThrewException](1126-invokedmethodthrewexception.md)|Сведения|Возникло исключение в методе, вызванном операцией «%1». %2|WFRuntime|  
|[1131 — InvokeMethodUseAsyncPattern](1131-invokemethoduseasyncpattern.md)|Сведения|Метод InvokeMethod «%1»: в методе используется асинхронная модель «%2» и «%3».|WFRuntime|  
|[1132 — InvokeMethodDoesNotUseAsyncPattern](1132-invokemethoddoesnotuseasyncpattern.md)|Сведения|Метод InvokeMethod «%1»: в методе не используется асинхронная модель.|WFRuntime|  
|[1140 — FlowchartStart](1140-flowchartstart.md)|Сведения|Блок-схема «%1»: запуск запланирован.|WFActivities|  
|[1141 — FlowchartEmpty](1141-flowchartempty.md)|Предупреждение|Блок-схема «%1» выполнена без узлов. В методе, вызванном действием «%1», возникло исключение. %2|WFActivities|  
|[1143 — FlowchartNextNull](1143-flowchartnextnull.md)|Сведения|Блок-схема «%1»/FlowStep - следующий узел имеет значение NULL. Выполнение блок-схемы будет завершено.|WFActivities|  
|[1146 — FlowchartSwitchCase](1146-flowchartswitchcase.md)|Сведения|Блок-схема «%1»/FlowSwitch: выбран вариант Case «%2».|WFActivities|  
|[1147 — FlowchartSwitchDefault](1147-flowchartswitchdefault.md)|Сведения|Блок-схема «%1»/FlowSwitch: выбрано действие Default Case.|WFActivities|  
|[1148 — FlowchartSwitchCaseNotFound](1148-flowchartswitchcasenotfound.md)|Сведения|Блок-схема «%1»/FlowSwitch - не удалось найти ни действие Case, ни действие Default Case, соответствующее результату выражения Expression. Выполнение блок-схемы будет завершено.|WFActivities|  
|[1150 — CompensationState](1150-compensationstate.md)|Сведения|CompensableActivity «%1» находится в состоянии «%2».|WFActivities|  
|[1223 — SwitchCaseNotFound](1223-switchcasenotfound.md)|Сведения|Действию Switch «%1» не удалось найти действие Case, соответствующее результату выражения Expression.|WFActivities|  
|[1449 — WfMessageReceived](1449-wfmessagereceived.md)|Сведения|Сообщение, полученное рабочим процессом|WFServices|  
|[1450 — WfMessageSent](1450-wfmessagesent.md)|Сведения|Сообщение, отправленное из рабочего процесса|WFServices|  
|[2021 — ExecuteWorkItemStart](2021-executeworkitemstart.md)|Verbose|Запуск выполнения рабочего элемента|WFRuntime|  
|[2022 — ExecuteWorkItemStop](2022-executeworkitemstop.md)|Verbose|Остановка выполнения рабочего элемента|WFRuntime|  
|[2023 — SendMessageChannelCacheMiss](2023-sendmessagechannelcachemiss.md)|Verbose|Промах SendMessageChannelCache|WFRuntime|  
|[2024 — InternalCacheMetadataStart](2024-internalcachemetadatastart.md)|Verbose|InternalCacheMetadata запущено в действии «%1».|WFRuntime|  
|[2025 — InternalCacheMetadataStop](2025-internalcachemetadatastop.md)|Verbose|InternalCacheMetadata остановлено для действия «%1».|WFRuntime|  
|[2026 — CompileVbExpressionStart](2026-compilevbexpressionstart.md)|Verbose|Компиляция выражения VB «%1»|WFRuntime|  
|[2027 — CacheRootMetadataStart](2027-cacherootmetadatastart.md)|Verbose|CacheRootMetadata запущено для действия «%1»|WFRuntime|  
|[2028 — CacheRootMetadataStop](2028-cacherootmetadatastop.md)|Verbose|CacheRootMetadata остановлено для действия %1.|WFRuntime|  
|[2029 — CompileVbExpressionStop](2029-compilevbexpressionstop.md)|Verbose|Компиляция выражения VB завершена.|WFRuntime|  
|[2576 — TryCatchExceptionFromTry](2576-trycatchexceptionfromtry.md)|Сведения|В действии TryCatch «%1» было перехвачено исключение типа «%2».|WFActivities|  
|[2577 — TryCatchExceptionDuringCancelation](2577-trycatchexceptionduringcancelation.md)|Предупреждение|При отмене дочернего действия для действия TryCatch «%1» произошло исключение.|WFActivities|  
|[2578 — TryCatchExceptionFromCatchOrFinally](2578-trycatchexceptionfromcatchorfinally.md)|Предупреждение|В действии Catch или Finally, связанном с действием TryCatch «%1», произошло исключение.|WFActivities|  
|[3501 — InferredContractDescription](3501-inferredcontractdescription.md)|Сведения|Описание ContractDescription с параметрами Name=«%1» и Namespace=«%2» было выведено из WorkflowService.|WFServices|  
|[3502 — InferredOperationDescription](3502-inferredoperationdescription.md)|Сведения|Описание OperationDescription с параметром Name=«%1» в контракте «%2» было выведено из WorkflowService. IsOneWay=%3.|WFServices|  
|[3503 — DuplicateCorrelationQuery](3503-duplicatecorrelationquery.md)|Предупреждение|Обнаружен повторяющийся запрос CorrelationQuery с параметром Where=«%1». Это дубликат не будет использоваться при расчете корреляции.|WFServices|  
|[3507 — ServiceEndpointAdded](3507-serviceendpointadded.md)|Сведения|Конечная точка службы была добавлена для адреса «%1», привязки «%2» и контракта «%3».|WFServices|  
|[3508 — TrackingProfileNotFound](3508-trackingprofilenotfound.md)|Verbose|Не найден TrackingProfile «%1» для ActivityDefinitionId «%2». Профиль TrackingProfile не найден в файле конфигурации, или обнаружено несоответствие ActivityDefinitionId.|WFServices|  
|[3550 — BufferOutOfOrderMessageNoInstance](3550-bufferoutofordermessagenoinstance.md)|Сведения|Операция «%1» сейчас не может быть выполнена. Следующая попытка будет предпринята, когда экземпляр службы будет готов к обработке именно этой операции.|WFServices|  
|[3551 — BufferOutOfOrderMessageNoBookmark](3551-bufferoutofordermessagenobookmark.md)|Сведения|Операция «%2» в экземпляре службы «%1» не может быть выполнена в данный момент. Следующая попытка будет предпринята, когда экземпляр службы будет готов к обработке именно этой операции.|WFServices|  
|[3552 — MaxPendingMessagesPerChannelExceeded](3552-maxpendingmessagesperchannelexceeded.md)|Предупреждение|Регулирования «MaxPendingMessagesPerChannel» ограничение «%1» был нажат. Для увеличения этого предела настройте свойство MaxPendingMessagesPerChannel для поведения BufferedReceiveServiceBehavior.|Квота WFServices|  
|[3557 — TransactedReceiveScopeEndCommitFailed](3557-transactedreceivescopeendcommitfailed.md)|Сведения|Вызов EndCommit для CommittableTransaction с id = «%1» привел к созданию исключения TransactionException со следующим сообщением: «%2».|WFServices|  
|[4201 — EndSqlCommandExecute](4201-endsqlcommandexecute.md)|Verbose|Окончание выполнения команды SQL: %1|WFInstanceStore|  
|[4202 — StartSqlCommandExecute](4202-startsqlcommandexecute.md)|Verbose|Запуск выполнения команды SQL: %1|WFInstanceStore|  
|[4203 — RenewLockSystemError](4203-renewlocksystemerror.md)|Error|Не удалось увеличить срок окончания блокировки, срок окончания блокировки уже истек или владелец блокировки удален. Прерывание блокировки SqlWorkflowInstanceStore.|WFInstanceStore|  
|[4205 — FoundProcessingError](4205-foundprocessingerror.md)|Error|Не удалось выполнить команду: %1|WFInstanceStore|  
|[4206 — UnlockInstanceException](4206-unlockinstanceexception.md)|Error|При попытке разблокировать экземпляр обнаружено исключение «%1».|WFInstanceStore|  
|[4207 — MaximumRetriesExceededForSqlCommand](4207-maximumretriesexceededforsqlcommand.md)|Сведения|Выполнено максимальное количество повторов команды SQL. Дальнейшие попытки выполняться не будут.|Квота WFInstanceStore|  
|[4208 — RetryingSqlCommandDueToSqlError](4208-retryingsqlcommandduetosqlerror.md)|Сведения|Выполняется повтор команды SQL из-за ошибки SQL с номером %1.|WFInstanceStore|  
|[4209 — TimeoutOpeningSqlConnection](4209-timeoutopeningsqlconnection.md)|Error|Истекло время ожидания при открытии соединения SQL. Не удалось выполнить операцию за выделенное время ожидания %1. Возможно, выделенное для этой операции время было частью более длительного времени ожидания.|WFInstanceStore|  
|[4210 — SqlExceptionCaught](4210-sqlexceptioncaught.md)|Предупреждение|Обнаружено исключение SQL с номером %1, сообщение %2.|WFInstanceStore|  
|[4211 — QueuingSqlRetry](4211-queuingsqlretry.md)|Предупреждение|Повторная попытка поместить SQL в очередь с задержкой %1 мс.|WFInstanceStore|  
|[4212 — LockRetryTimeout](4212-lockretrytimeout.md)|Предупреждение|Время ожидания при попытке получить блокировку для экземпляра.  Не удалось выполнить операцию за выделенное время ожидания %1. Возможно, выделенное для этой операции время было частью более длительного времени ожидания.|WFInstanceStore|  
|[4213 — RunnableInstancesDetectionError](4213-runnableinstancesdetectionerror.md)|Error|Не удалось обнаружить доступные для выполнения экземпляры, поскольку обнаружено следующее исключение|WFInstanceStore|  
|[4214 — InstanceLocksRecoveryError](4214-instancelocksrecoveryerror.md)|Error|Не удалось восстановить блокировки экземпляров, поскольку обнаружено следующее исключение|WFInstanceStore|  
|[39456 — TrackingRecordDropped](39456-trackingrecorddropped.md)|Предупреждение|Размер записи отслеживания %1 превышает максимально допустимое значение, разрешенное в сеансе трассировки событий Windows для поставщика %2|WFTracking|  
|[39457 — TrackingRecordRaised](39457-trackingrecordraised.md)|Сведения|Запись отслеживания %1 повышена до %2.|WFRuntime|  
|[39458 — TrackingRecordTruncated](39458-trackingrecordtruncated.md)|Предупреждение|Усеченная запись отслеживания %1 записана в сеанс трассировки событий Windows с использованием поставщика %2. Данные переменных, заметок, пользователей удалены|WFTracking|  
|[39459 — TrackingDataExtracted](39459-trackingdataextracted.md)|Verbose|Отслеживание данных %1, извлеченных в действии %2.|WFRuntime|  
|[39460 — TrackingValueNotSerializable](39460-trackingvaluenotserializable.md)|Предупреждение|Извлеченный аргумент или переменная «%1» не сериализуется.|WFTracking|  
|[57398 — MaxInstancesExceeded](57398-maxinstancesexceeded.md)|Предупреждение|Система достигла предела, заданного для ограничителя «MaxConcurrentInstances». Для этого ограничителя был задан предел %1. Значение ограничителя можно изменить, изменив атрибут maxConcurrentInstances в элементе serviceThrottle или свойство MaxConcurrentInstances для поведения ServiceThrottlingBehavior.|WFServices|
