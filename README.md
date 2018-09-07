# sham 
<Activity mc:Ignorable="sad" x:Class="TfsBuild.Process" xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:mt="clr-namespace:Microsoft.TeamFoundation;assembly=Microsoft.TeamFoundation.Common" xmlns:mtbc="clr-namespace:Microsoft.TeamFoundation.Build.Client;assembly=Microsoft.TeamFoundation.Build.Client" xmlns:mtbw="clr-namespace:Microsoft.TeamFoundation.Build.Workflow;assembly=Microsoft.TeamFoundation.Build.Workflow" xmlns:mtbwa="clr-namespace:Microsoft.TeamFoundation.Build.Workflow.Activities;assembly=Microsoft.TeamFoundation.Build.Workflow" xmlns:mtbwt="clr-namespace:Microsoft.TeamFoundation.Build.Workflow.Tracking;assembly=Microsoft.TeamFoundation.Build.Workflow" xmlns:mttbb="clr-namespace:Microsoft.TeamFoundation.TestImpact.BuildIntegration.BuildActivities;assembly=Microsoft.TeamFoundation.TestImpact.BuildIntegration" xmlns:mtvc="clr-namespace:Microsoft.TeamFoundation.VersionControl.Client;assembly=Microsoft.TeamFoundation.VersionControl.Client" xmlns:mtvco="clr-namespace:Microsoft.TeamFoundation.VersionControl.Common;assembly=Microsoft.TeamFoundation.VersionControl.Common" xmlns:mva="clr-namespace:Microsoft.VisualBasic.Activities;assembly=System.Activities" xmlns:s="clr-namespace:System;assembly=mscorlib" xmlns:sad="http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation" xmlns:sad1="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib" xmlns:sl="clr-namespace:System.Linq;assembly=System.Core" xmlns:this="clr-namespace:TfsBuild;" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <x:Members>
    <x:Property Name="BuildSettings" Type="InArgument(mtbwa:BuildSettings)" />
    <x:Property Name="TestSpecs" Type="InArgument(mtbwa:TestSpecList)" />
    <x:Property Name="BuildNumberFormat" Type="InArgument(x:String)" />
    <x:Property Name="SolutionSpecificBuildOutputs" Type="InArgument(x:Boolean)" />
    <x:Property Name="CleanWorkspace" Type="InArgument(mtbwa:CleanWorkspaceOption)" />
    <x:Property Name="RunCodeAnalysis" Type="InArgument(mtbwa:CodeAnalysisOption)" />
    <x:Property Name="SourceAndSymbolServerSettings" Type="InArgument(mtbwa:SourceAndSymbolServerSettings)" />
    <x:Property Name="AgentSettings" Type="InArgument(mtbwa:AgentSettings)" />
    <x:Property Name="AssociateChangesetsAndWorkItems" Type="InArgument(x:Boolean)" />
    <x:Property Name="CreateWorkItem" Type="InArgument(x:Boolean)" />
    <x:Property Name="MSBuildArguments" Type="InArgument(x:String)" />
    <x:Property Name="MSBuildPlatform" Type="InArgument(mtbwa:ToolPlatform)" />
    <x:Property Name="MSBuildMultiProc" Type="InArgument(x:Boolean)" />
    <x:Property Name="PerformTestImpactAnalysis" Type="InArgument(x:Boolean)" />
    <x:Property Name="CreateLabel" Type="InArgument(x:Boolean)" />
    <x:Property Name="DisableTests" Type="InArgument(x:Boolean)" />
    <x:Property Name="GetVersion" Type="InArgument(x:String)" />
    <x:Property Name="PrivateDropLocation" Type="InArgument(x:String)" />
    <x:Property Name="Verbosity" Type="InArgument(mtbw:BuildVerbosity)" />
    <x:Property Name="Metadata" Type="mtbw:ProcessParameterMetadataCollection" />
    <x:Property Name="SupportedReasons" Type="mtbc:BuildReason" />
    <x:Property Name="BuildProcessVersion" Type="x:String" />
  </x:Members>
  <this:Process.BuildSettings>[New Microsoft.TeamFoundation.Build.Workflow.Activities.BuildSettings()]</this:Process.BuildSettings>
  <this:Process.DisableTests>[False]</this:Process.DisableTests>
  <this:Process.TestSpecs>[New Microsoft.TeamFoundation.Build.Workflow.Activities.TestSpecList(New Microsoft.TeamFoundation.Build.Workflow.Activities.AgileTestPlatformSpec("**\*test*.dll"))]</this:Process.TestSpecs>
  <this:Process.BuildNumberFormat>["$(BuildDefinitionName)_$(Date:yyyyMMdd)$(Rev:.r)"]</this:Process.BuildNumberFormat>
  <this:Process.SolutionSpecificBuildOutputs>[False]</this:Process.SolutionSpecificBuildOutputs>
  <this:Process.AssociateChangesetsAndWorkItems>[True]</this:Process.AssociateChangesetsAndWorkItems>
  <this:Process.CreateWorkItem>[True]</this:Process.CreateWorkItem>
  <this:Process.CleanWorkspace>[Microsoft.TeamFoundation.Build.Workflow.Activities.CleanWorkspaceOption.All]</this:Process.CleanWorkspace>
  <this:Process.MSBuildArguments>
    <InArgument x:TypeArguments="x:String" />
  </this:Process.MSBuildArguments>
  <this:Process.RunCodeAnalysis>[Microsoft.TeamFoundation.Build.Workflow.Activities.CodeAnalysisOption.AsConfigured]</this:Process.RunCodeAnalysis>
  <this:Process.MSBuildMultiProc>[True]</this:Process.MSBuildMultiProc>
  <this:Process.MSBuildPlatform>[Microsoft.TeamFoundation.Build.Workflow.Activities.ToolPlatform.Auto]</this:Process.MSBuildPlatform>
  <this:Process.PerformTestImpactAnalysis>[False]</this:Process.PerformTestImpactAnalysis>
  <this:Process.SourceAndSymbolServerSettings>[New Microsoft.TeamFoundation.Build.Workflow.Activities.SourceAndSymbolServerSettings(True, Nothing)]</this:Process.SourceAndSymbolServerSettings>
  <this:Process.CreateLabel>[True]</this:Process.CreateLabel>
  <this:Process.GetVersion>
    <InArgument x:TypeArguments="x:String" />
  </this:Process.GetVersion>
  <this:Process.AgentSettings>[New Microsoft.TeamFoundation.Build.Workflow.Activities.AgentSettings() With {.MaxWaitTime = New System.TimeSpan(4, 0, 0), .MaxExecutionTime = New System.TimeSpan(0, 0, 0), .TagComparison = Microsoft.TeamFoundation.Build.Workflow.Activities.TagComparison.MatchExactly }]</this:Process.AgentSettings>
  <this:Process.Verbosity>[Microsoft.TeamFoundation.Build.Workflow.BuildVerbosity.Normal]</this:Process.Verbosity>
  <this:Process.Metadata>
    <mtbw:ProcessParameterMetadataCollection>
      <mtbw:ProcessParameterMetadata BrowsableWhen="EditingDefinition" Category="#300 Advanced" DisplayName="MSBuild Multi-Proc" Description="Enable MSBuild Multi-proc to build your solutions' projects in parallel, when possible, using all available processors on the build server." ParameterName="MSBuildMultiProc" />
      <mtbw:ProcessParameterMetadata BrowsableWhen="EditingDefinition" Category="#300 Advanced" DisplayName="Solution Specific Build Outputs" Description="True will put build outputs into folders based on the solution name. False will put all build outputs into the same folder." ParameterName="SolutionSpecificBuildOutputs" />
    </mtbw:ProcessParameterMetadataCollection>
  </this:Process.Metadata>
  <this:Process.SupportedReasons>All</this:Process.SupportedReasons>
  <this:Process.BuildProcessVersion>11.0</this:Process.BuildProcessVersion>
  <mva:VisualBasic.Settings>Assembly references and imported namespaces serialized as XML namespaces</mva:VisualBasic.Settings>
  <Sequence mtbwt:BuildTrackingParticipant.Importance="None">
    <Sequence.Variables>
      <Variable x:TypeArguments="mtbc:IBuildDetail" Name="BuildDetail" />
      <Variable x:TypeArguments="x:String" Name="DropLocation" />
    </Sequence.Variables>
    <mtbwa:GetBuildDetail DisplayName="Get the Build" Result="[BuildDetail]" mtbwt:BuildTrackingParticipant.Importance="Low" />
    <Sequence DisplayName="Update Drop Location" mtbwt:BuildTrackingParticipant.Importance="Low">
      <mtbwa:InvokeForReason DisplayName="Update Build Number for Triggered Builds" Reason="Triggered">
        <mtbwa:UpdateBuildNumber BuildNumberFormat="[BuildNumberFormat]" DisplayName="Update Build Number" />
      </mtbwa:InvokeForReason>
      <If Condition="[(Not String.IsNullOrEmpty(BuildDetail.DropLocationRoot)) AndAlso (BuildDetail.Reason And Microsoft.TeamFoundation.Build.Client.BuildReason.Triggered) = BuildDetail.Reason]" DisplayName="If Build Reason is Triggered" mtbwt:BuildTrackingParticipant.Importance="Low">
        <If.Then>
          <Sequence mtbwt:BuildTrackingParticipant.Importance="None">
            <Assign x:TypeArguments="x:String" mtbwt:BuildTrackingParticipant.Importance="None" Value="[BuildDropProvider.CombinePaths(BuildDetail.DropLocationRoot, BuildDetail.BuildDefinition.Name, BuildDetail.BuildNumber)]" To="[DropLocation]" />
            <mtbwa:SetBuildProperties DisplayName="Set Drop Location" DropLocation="[DropLocation]" PropertiesToSet="DropLocation" mtbwt:BuildTrackingParticipant.Importance="Low" />
          </Sequence>
        </If.Then>
      </If>
      <If Condition="[(Not String.IsNullOrEmpty(PrivateDropLocation)) AndAlso BuildDetail.Reason = Microsoft.TeamFoundation.Build.Client.BuildReason.ValidateShelveset]" DisplayName="If Build Reason is ValidateShelveset" mtbwt:BuildTrackingParticipant.Importance="Low">
        <If.Then>
          <Sequence mtbwt:BuildTrackingParticipant.Importance="None">
            <Assign x:TypeArguments="x:String" Value="[BuildDropProvider.CombinePaths(PrivateDropLocation, BuildDetail.BuildDefinition.Name, BuildDetail.BuildNumber)]" To="[DropLocation]" mtbwt:BuildTrackingParticipant.Importance="None" />
            <mtbwa:SetBuildProperties DisplayName="Set Drop Location for Private Build" DropLocation="[DropLocation]" PropertiesToSet="DropLocation" mtbwt:BuildTrackingParticipant.Importance="Low" />
          </Sequence>
        </If.Then>
      </If>
    </Sequence>
    <mtbwa:AgentScope DisplayName="Run On Agent" MaxExecutionTime="[AgentSettings.MaxExecutionTime]" MaxWaitTime="[AgentSettings.MaxWaitTime]" ReservationSpec="[AgentSettings.GetAgentReservationSpec()]">
      <mtbwa:AgentScope.Variables>
        <Variable x:TypeArguments="mtbc:IBuildAgent" Name="BuildAgent" />
        <Variable x:TypeArguments="mtvc:Workspace" Name="Workspace" />
        <Variable x:TypeArguments="x:String" Name="BuildDirectory" />
        <Variable x:TypeArguments="x:String" Default="[BuildDetail.BuildNumber]" Name="LabelName" />
        <Variable x:TypeArguments="x:String" Name="WorkspaceName" />
        <Variable x:TypeArguments="x:String" Name="SourcesDirectory" />
        <Variable x:TypeArguments="x:String" Name="BinariesDirectory" />
        <Variable x:TypeArguments="x:String" Name="TestResultsDirectory" />
      </mtbwa:AgentScope.Variables>
      <Sequence DisplayName="Initialize Variables" mtbwt:BuildTrackingParticipant.Importance="Low">
        <mtbwa:GetBuildAgent DisplayName="Get the Agent" Result="[BuildAgent]" mtbwt:BuildTrackingParticipant.Importance="Low" />
        <mtbwa:GetBuildDirectory DisplayName="Get the Build Directory" Result="[BuildDirectory]" mtbwt:BuildTrackingParticipant.Importance="Low" />
        <Assign x:TypeArguments="x:String" DisplayName="Initialize Workspace Name" To="[WorkspaceName]" Value="[String.Format(&quot;{0}_{1}_{2}&quot;, BuildDetail.BuildDefinition.Id, Microsoft.TeamFoundation.LinkingUtilities.DecodeUri(BuildAgent.Uri.AbsoluteUri).ToolSpecificId, BuildAgent.ServiceHost.Name)]" mtbwt:BuildTrackingParticipant.Importance="Low" />
        <Assign x:TypeArguments="x:String" DisplayName="Initialize Sources Directory" To="[SourcesDirectory]" Value="[String.Format(&quot;{0}\src&quot;, BuildDirectory)]" mtbwt:BuildTrackingParticipant.Importance="Low" />
        <Assign x:TypeArguments="x:String" DisplayName="Initialize Binaries Directory" To="[BinariesDirectory]" Value="[String.Format(&quot;{0}\bin&quot;, BuildDirectory)]" mtbwt:BuildTrackingParticipant.Importance="Low" />
        <Assign x:TypeArguments="x:String" DisplayName="Initialize TestResults Directory" To="[TestResultsDirectory]" Value="[String.Format(&quot;{0}\tst&quot;, BuildDirectory)]" mtbwt:BuildTrackingParticipant.Importance="Low" />
        <If Condition="[Not BuildSettings.HasPlatformConfigurations]" DisplayName="If Not BuildSettings.HasPlatformConfigurations" mtbwt:BuildTrackingParticipant.Importance="Low">
          <If.Then>
            <AddToCollection x:TypeArguments="mtbwa:PlatformConfiguration" DisplayName="Use Default Platform Configuration" Collection="[BuildSettings.PlatformConfigurations]" Item="[Microsoft.TeamFoundation.Build.Workflow.Activities.PlatformConfiguration.Default]" mtbwt:BuildTrackingParticipant.Importance="Low" />
          </If.Then>
        </If>
        <If Condition="[WorkspaceName.Length &gt; Microsoft.TeamFoundation.VersionControl.Common.RepositoryConstants.MaxWorkspaceNameSize]" DisplayName="If WorkspaceName &gt; MaxSize" mtbwt:BuildTrackingParticipant.Importance="Low">
          <If.Then>
            <Sequence mtbwt:BuildTrackingParticipant.Importance="None">
              <mtbwa:WriteBuildWarning DisplayName="Write Workspace Size Warning" Message="[String.Format(&quot;The workspace name '{0}' exceeds the maximum allowed limit of '{1}' characters. Truncating it to match the maximum limit.&quot;, WorkspaceName, Microsoft.TeamFoundation.VersionControl.Common.RepositoryConstants.MaxWorkspaceNameSize)]" />
              <Assign x:TypeArguments="x:String" DisplayName="Truncate WorkspaceName to MaxSize" To="[WorkspaceName]" Value="[WorkspaceName.Substring(0, Microsoft.TeamFoundation.VersionControl.Common.RepositoryConstants.MaxWorkspaceNameSize).TrimEnd()]" mtbwt:BuildTrackingParticipant.Importance="Low" />
            </Sequence>
          </If.Then>
        </If>
      </Sequence>
      <Sequence DisplayName="Initialize Workspace" mtbwt:BuildTrackingParticipant.Importance="Low">
        <mtbwa:DeleteDirectory Directory="[TestResultsDirectory]" DisplayName="Delete Test Results Directory" Recursive="[True]" mtbwt:BuildTrackingParticipant.Importance="Low" />
        <If Condition="[Not CleanWorkspace = Microsoft.TeamFoundation.Build.Workflow.Activities.CleanWorkspaceOption.None]" DisplayName="If Not CleanWorkspace = CleanWorkspaceOption.None" mtbwt:BuildTrackingParticipant.Importance="Low">
          <If.Then>
            <mtbwa:DeleteDirectory Directory="[BinariesDirectory]" DisplayName="Delete Binaries Directory" mtbwt:BuildTrackingParticipant.Importance="Low" />
          </If.Then>
        </If>
        <If Condition="[CleanWorkspace = Microsoft.TeamFoundation.Build.Workflow.Activities.CleanWorkspaceOption.All]" DisplayName="If CleanWorkspace = CleanWorkspaceOption.All" mtbwt:BuildTrackingParticipant.Importance="Low">
          <If.Then>
            <Sequence DisplayName="Delete Workspace and Sources Directory" mtbwt:BuildTrackingParticipant.Importance="Low">
              <mtbwa:DeleteWorkspace DeleteLocalItems="[True]" DisplayName="Delete Workspace" Name="[WorkspaceName]" mtbwt:BuildTrackingParticipant.Importance="Low" />
              <mtbwa:DeleteDirectory Directory="[SourcesDirectory]" DisplayName="Delete Sources Directory" mtbwt:BuildTrackingParticipant.Importance="Low" />
            </Sequence>
          </If.Then>
        </If>
        <mtbwa:CreateWorkspace BuildDirectory="[BuildDirectory]" Comment="[&quot;Workspace Created by Team Build&quot;]" DisplayName="Create Workspace" Name="[WorkspaceName]" Result="[Workspace]" SourcesDirectory="[SourcesDirectory]" />
        <If Condition="[CleanWorkspace = Microsoft.TeamFoundation.Build.Workflow.Activities.CleanWorkspaceOption.Outputs]" DisplayName="If CleanWorkspace = CleanWorkspaceOption.Outputs" mtbwt:BuildTrackingParticipant.Importance="Low">
          <If.Then>
            <ForEach x:TypeArguments="mtbwa:PlatformConfiguration" DisplayName="For Each Configuration in BuildSettings.PlatformConfigurations" Values="[BuildSettings.PlatformConfigurations]" mtbwt:BuildTrackingParticipant.Importance="Low">
              <ActivityAction x:TypeArguments="mtbwa:PlatformConfiguration">
                <ActivityAction.Argument>
                  <DelegateInArgument x:TypeArguments="mtbwa:PlatformConfiguration" Name="platformConfiguration" />
                </ActivityAction.Argument>
                <Sequence DisplayName="Clean Configuration">
                  <If Condition="[BuildSettings.HasProjectsToBuild]" DisplayName="If BuildSettings.HasProjectsToBuild" mtbwt:BuildTrackingParticipant.Importance="Low">
                    <If.Then>
                      <ForEach x:TypeArguments="x:String" DisplayName="For Each Project in BuildSettings.ProjectsToBuild" Values="[BuildSettings.ProjectsToBuild]" mtbwt:BuildTrackingParticipant.Importance="Low">
                        <ActivityAction x:TypeArguments="x:String">
                          <ActivityAction.Argument>
                            <DelegateInArgument x:TypeArguments="x:String" Name="serverBuildProjectItem" />
                          </ActivityAction.Argument>
                          <Sequence DisplayName="Clean Project" mtbwt:BuildTrackingParticipant.Importance="Low">
                            <Sequence.Variables>
                              <Variable x:TypeArguments="x:String" Name="localBuildProjectItem" />
                            </Sequence.Variables>
                            <mtbwa:ConvertWorkspaceItem DisplayName="Convert Server Paths to Local Paths" Input="[serverBuildProjectItem]" Result="[localBuildProjectItem]" Workspace="[Workspace]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                            <If Condition="[System.IO.File.Exists(localBuildProjectItem)]" DisplayName="If File.Exists(Project)" mtbwt:BuildTrackingParticipant.Importance="Low">
                              <If.Then>
                                <mtbwa:MSBuild CommandLineArguments="[String.Format(&quot;/p:SkipInvalidConfigurations=true {0}&quot;, MSBuildArguments)]" Configuration="[platformConfiguration.Configuration]" DisplayName="Run MSBuild for Project" GenerateVSPropsFile="[True]" MaxProcesses="[If (MSBuildMultiProc, 0, 1)]" OutDir="[BinariesDirectory]" Platform="[platformConfiguration.Platform]" Project="[localBuildProjectItem]" Targets="[New String() { &quot;Clean&quot; }]" TargetsNotLogged="[New String() {&quot;GetNativeManifest&quot;, &quot;GetCopyToOutputDirectoryItems&quot;, &quot;GetTargetPath&quot;}]" ToolPlatform="[MSBuildPlatform]" Verbosity="[Verbosity]" />
                              </If.Then>
                            </If>
                          </Sequence>
                        </ActivityAction>
                      </ForEach>
                    </If.Then>
                  </If>
                </Sequence>
              </ActivityAction>
            </ForEach>
          </If.Then>
        </If>
        <mtbwa:SyncWorkspace DisplayName="Get Workspace" VersionOverride="[GetVersion]" Workspace="[Workspace]">
          <mtbwa:SyncWorkspace.RequestsFailed>
            <ActivityAction x:TypeArguments="scg:ICollection(mtbc:IQueuedBuild)">
              <ActivityAction.Argument>
                <DelegateInArgument x:TypeArguments="scg:ICollection(mtbc:IQueuedBuild)" Name="failedRequests" />
              </ActivityAction.Argument>
              <mtbwa:RetryRequests Behavior="[Microsoft.TeamFoundation.Build.Workflow.Activities.RetryBehavior.DoNotBatch]" DisplayName="Mark Requests for Retry" Requests="[failedRequests]" mtbwt:BuildTrackingParticipant.Importance="Low" />
            </ActivityAction>
          </mtbwa:SyncWorkspace.RequestsFailed>
        </mtbwa:SyncWorkspace>
      </Sequence>
      <If Condition="[CreateLabel]" DisplayName="If CreateLabel" mtbwt:BuildTrackingParticipant.Importance="Low">
        <If.Then>
          <mtbwa:InvokeForReason DisplayName="Create and Set Label for non-Shelveset Builds" Reason="Manual, IndividualCI, BatchedCI, Schedule, ScheduleForced, UserCreated">
            <mtbwa:LabelWorkspace Comment="[&quot;Label Created by Team Build&quot;]" DisplayName="Create Label" Name="[LabelName]" Scope="[String.Format(&quot;$/{0}&quot;, BuildDetail.BuildDefinition.TeamProject)]" Workspace="[Workspace]" />
            <mtbwa:SetBuildProperties DisplayName="Set Label on BuildDetail" LabelName="[String.Format(&quot;{0}@$/{1}&quot;, LabelName, BuildDetail.BuildDefinition.TeamProject)]" PropertiesToSet="LabelName" mtbwt:BuildTrackingParticipant.Importance="Low" />
          </mtbwa:InvokeForReason>
        </If.Then>
        <If.Else>
          <mtbwa:WriteBuildMessage DisplayName="Write Message" Message="Not Labeling sources" Importance="[Microsoft.TeamFoundation.Build.Client.BuildMessageImportance.High]" />
        </If.Else>
      </If>
      <TryCatch DisplayName="Try Compile, Test, and Associate Changesets and Work Items" mtbwt:BuildTrackingParticipant.Importance="Low">
        <TryCatch.Finally>
          <Sequence DisplayName="Revert Workspace and Copy Files to Drop Location" mtbwt:BuildTrackingParticipant.Importance="Low">
            <mtbwa:InvokeForReason DisplayName="Revert Workspace for Shelveset Builds" Reason="CheckInShelveset, ValidateShelveset">
              <mtbwa:RevertWorkspace DisplayName="Revert Workspace" Workspace="[Workspace]" />
            </mtbwa:InvokeForReason>
            <If Condition="[Not String.IsNullOrEmpty(DropLocation)]" DisplayName="If DropLocation is Set" mtbwt:BuildTrackingParticipant.Importance="Low">
              <If.Then>
                <mtbwa:CopyDirectory DisplayName="Drop Files to Drop Location" Source="[BinariesDirectory]" Destination="[DropLocation]" />
              </If.Then>
            </If>
          </Sequence>
        </TryCatch.Finally>
        <TryCatch.Try>
          <Sequence mtbwt:BuildTrackingParticipant.Importance="None">
            <Sequence.Variables>
              <Variable x:TypeArguments="s:Exception" Name="compilationException" />
              <Variable x:TypeArguments="scg:IList(mtvc:Changeset)" Name="associatedChangesets" />
              <Variable x:TypeArguments="s:Boolean" Name="treatTestFailureAsBuildFailure" />
            </Sequence.Variables>
            <Parallel DisplayName="Compile, Test, and Associate Changesets and Work Items">
              <TryCatch DisplayName="Try Compile and Test" mtbwt:BuildTrackingParticipant.Importance="Low">
                <TryCatch.Try>
                  <Sequence DisplayName="Compile and Test">
                    <ForEach x:TypeArguments="mtbwa:PlatformConfiguration" DisplayName="For Each Configuration in BuildSettings.PlatformConfigurations" Values="[BuildSettings.PlatformConfigurations]" mtbwt:BuildTrackingParticipant.Importance="Low">
                      <ActivityAction x:TypeArguments="mtbwa:PlatformConfiguration">
                        <ActivityAction.Argument>
                          <DelegateInArgument x:TypeArguments="mtbwa:PlatformConfiguration" Name="platformConfiguration" />
                        </ActivityAction.Argument>
                        <Sequence DisplayName="Compile and Test for Configuration" mtbwt:BuildTrackingParticipant.Importance="Low">
                          <Sequence.Variables>
                            <Variable x:TypeArguments="x:String" Name="outputDirectory" />
                            <Variable x:TypeArguments="x:String" Name="logFileDropLocation" />
                          </Sequence.Variables>
                          <Sequence DisplayName="Initialize Variables" mtbwt:BuildTrackingParticipant.Importance="Low">
                            <Assign x:TypeArguments="x:String" DisplayName="Create OutputDirectory Per Platform and Configuration" To="[outputDirectory]" Value="[If (platformConfiguration.IsEmpty Or BuildSettings.PlatformConfigurations.Count = 1, BinariesDirectory, If (platformConfiguration.IsPlatformEmptyOrAnyCpu, BinariesDirectory + &quot;\&quot; + platformConfiguration.Configuration, BinariesDirectory + &quot;\&quot; + platformConfiguration.Platform + &quot;\&quot; + platformConfiguration.Configuration))]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                            <If Condition="[Not String.IsNullOrEmpty(DropLocation)]" DisplayName="If DropLocation is Set" mtbwt:BuildTrackingParticipant.Importance="Low">
                              <If.Then>
                                <Assign x:TypeArguments="x:String" DisplayName="Initialize LogFile Drop Location" To="[logFileDropLocation]" Value="[If (platformConfiguration.IsEmpty Or BuildSettings.PlatformConfigurations.Count = 1, BuildDropProvider.CombinePaths(DropLocation, &quot;logs&quot;), If (platformConfiguration.IsPlatformEmptyOrAnyCpu, BuildDropProvider.CombinePaths(DropLocation, &quot;logs&quot;, platformConfiguration.Configuration), BuildDropProvider.CombinePaths(DropLocation, &quot;logs&quot;, platformConfiguration.Platform, platformConfiguration.Configuration)))]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                              </If.Then>
                            </If>
                          </Sequence>
                          <If Condition="[BuildSettings.HasProjectsToBuild]" DisplayName="If BuildSettings.HasProjectsToBuild" mtbwt:BuildTrackingParticipant.Importance="Low">
                            <If.Then>
                              <ForEach x:TypeArguments="x:String" DisplayName="For Each Project in BuildSettings.ProjectsToBuild" Values="[BuildSettings.ProjectsToBuild]" mtbwt:BuildTrackingParticipant.Importance="Low">
                                <ActivityAction x:TypeArguments="x:String">
                                  <ActivityAction.Argument>
                                    <DelegateInArgument x:TypeArguments="x:String" Name="serverBuildProjectItem" />
                                  </ActivityAction.Argument>
                                  <TryCatch DisplayName="Try to Compile the Project" mtbwt:BuildTrackingParticipant.Importance="Low">
                                    <TryCatch.Try>
                                      <Sequence DisplayName="Compile the Project" mtbwt:BuildTrackingParticipant.Importance="Low">
                                        <Sequence.Variables>
                                          <Variable x:TypeArguments="x:String" Name="localProject" />
                                          <Variable x:TypeArguments="x:String" Name="outputDirectoryPerProject" Default="[outputDirectory]" />
                                        </Sequence.Variables>
                                        <mtbwa:ConvertWorkspaceItem DisplayName="Convert Server Path to Local Path" Input="[serverBuildProjectItem]" Result="[localProject]" Workspace="[Workspace]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                        <If Condition="[SolutionSpecificBuildOutputs]" DisplayName="If Build Outputs are Solution-Specific" mtbwt:BuildTrackingParticipant.Importance="Low">
                                          <If.Then>
                                            <Sequence DisplayName="Update Output Directory" mtbwt:BuildTrackingParticipant.Importance="Low">
                                              <Assign x:TypeArguments="x:String" DisplayName="Set Solution-Specific Output Directory" To="[outputDirectoryPerProject]" Value="[System.IO.Path.Combine(outputDirectory, System.IO.Path.GetFileNameWithoutExtension(localProject))]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                              <If DisplayName="If Output Directory Exists" Condition="[System.IO.Directory.Exists(outputDirectoryPerProject)]" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                <If.Then>
                                                  <mtbwa:WriteBuildWarning DisplayName="Write Duplicate Project Names Warning" Message="[String.Format(&quot;{0} conflicts with another solution/project. Build outputs for solutions/projects with the same name will be copied to the same directory. To separate the build outputs, change the name of one of the solutions/projects.&quot;, System.IO.Path.GetFileNameWithoutExtension(localProject))]" />
                                                </If.Then>
                                              </If>
                                            </Sequence>
                                          </If.Then>
                                        </If>
                                        <mtbwa:MSBuild CommandLineArguments="[String.Format(&quot;/p:SkipInvalidConfigurations=true {0}&quot;, MSBuildArguments)]" Configuration="[platformConfiguration.Configuration]" DisplayName="Run MSBuild for Project" GenerateVSPropsFile="[True]" LogFileDropLocation="[logFileDropLocation]" MaxProcesses="[If (MSBuildMultiProc, 0, 1)]" OutDir="[outputDirectoryPerProject]" Platform="[platformConfiguration.Platform]" Project="[localProject]" RunCodeAnalysis="[RunCodeAnalysis]" TargetsNotLogged="[New String() {&quot;GetNativeManifest&quot;, &quot;GetCopyToOutputDirectoryItems&quot;, &quot;GetTargetPath&quot;}]" ToolPlatform="[MSBuildPlatform]" Verbosity="[Verbosity]" />
                                      </Sequence>
                                    </TryCatch.Try>
                                    <TryCatch.Catches>
                                      <Catch x:TypeArguments="s:Exception">
                                        <ActivityAction x:TypeArguments="s:Exception">
                                          <ActivityAction.Argument>
                                            <DelegateInArgument x:TypeArguments="s:Exception" Name="ex" />
                                          </ActivityAction.Argument>
                                          <Sequence DisplayName="Handle Exception">
                                            <Sequence.Variables>
                                              <Variable x:TypeArguments="scg:ICollection(mtbc:IQueuedBuild)" Name="failedRequests" />
                                            </Sequence.Variables>
                                            <mtbwa:SetBuildProperties CompilationStatus="[Microsoft.TeamFoundation.Build.Client.BuildPhaseStatus.Failed]" DisplayName="Set CompilationStatus to Failed" PropertiesToSet="CompilationStatus" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                            <If Condition="[CreateWorkItem]" DisplayName="If CreateWorkItem" mtbwt:BuildTrackingParticipant.Importance="Low">
                                              <If.Then>
                                                <mtbwa:InvokeForReason DisplayName="Create Work Item for non-Shelveset Builds" Reason="Manual, IndividualCI, BatchedCI, Schedule, ScheduleForced, UserCreated">
                                                  <mtbwa:OpenWorkItem AssignedTo="[BuildDetail.RequestedFor]" Comment="[&quot;This work item was created by TFS Build on a build failure.&quot;]" CustomFields="[New Dictionary(Of String, String) From { {&quot;System.Reason&quot;, &quot;Build Failure&quot;}, {&quot;Microsoft.VSTS.TCM.ReproSteps&quot;, &quot;Start the build using TFS Build&quot;}, {&quot;Severity&quot;, &quot;1 - Critical&quot;} }]" DisplayName="Create Work Item" Title="[String.Format(&quot;Build Failure in Build: {0}&quot;, BuildDetail.BuildNumber)]" Type="[&quot;Bug&quot;]" />
                                                </mtbwa:InvokeForReason>
                                              </If.Then>
                                            </If>
                                            <mtbwa:GetApprovedRequests DisplayName="Get Requests Approved for Check In" Result="[failedRequests]" mtbwt:BuildTrackingParticipant.Importance="None" />
                                            <mtbwa:RetryRequests Behavior="[Microsoft.TeamFoundation.Build.Workflow.Activities.RetryBehavior.DoNotBatch]" DisplayName="Mark Requests for Retry" Requests="[failedRequests]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                            <Rethrow DisplayName="Rethrow the exception so the build will stop" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                          </Sequence>
                                        </ActivityAction>
                                      </Catch>
                                    </TryCatch.Catches>
                                  </TryCatch>
                                </ActivityAction>
                              </ForEach>
                            </If.Then>
                          </If>
                          <If Condition="[Not DisableTests]" DisplayName="If Not DisableTests" mtbwt:BuildTrackingParticipant.Importance="Low">
                            <If.Then>
                              <Sequence DisplayName="Run Tests" mtbwt:BuildTrackingParticipant.Importance="Low">
                                <If Condition="[Not TestSpecs Is Nothing]" DisplayName="If Not TestSpecs Is Nothing" mtbwt:BuildTrackingParticipant.Importance="Low">
                                  <If.Then>
                                    <ForEach x:TypeArguments="mtbwa:TestSpec" DisplayName="For Each TestSpec in TestSpecs" Values="[TestSpecs]" mtbwt:BuildTrackingParticipant.Importance="Low">
                                      <ActivityAction x:TypeArguments="mtbwa:TestSpec">
                                        <ActivityAction.Argument>
                                          <DelegateInArgument x:TypeArguments="mtbwa:TestSpec" Name="spec" />
                                        </ActivityAction.Argument>
                                        <TryCatch DisplayName="Try Run Tests" mtbwt:BuildTrackingParticipant.Importance="Low">
                                          <TryCatch.Try>
                                            <If Condition="[TypeOf spec Is Microsoft.TeamFoundation.Build.Workflow.Activities.AgileTestPlatformSpec]" DisplayName="If spec Is AgileTestPlatformSpec" mtbwt:BuildTrackingParticipant.Importance="None">
                                              <If.Then>
                                                <Sequence DisplayName="Run Visual Studio Test Runner for Test Sources" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                  <Sequence.Variables>
                                                    <Variable x:TypeArguments="mtbwa:AgileTestPlatformSpec" Name="agileTestPlatformAssembly" />
                                                    <Variable x:TypeArguments="scg:IEnumerable(x:String)" Name="agileTestPlatformAssemblies" />
                                                  </Sequence.Variables>
                                                  <Assign x:TypeArguments="mtbwa:AgileTestPlatformSpec" DisplayName="Assign spec to agileTestPlatformAssembly" To="[agileTestPlatformAssembly]" Value="[DirectCast(spec, Microsoft.TeamFoundation.Build.Workflow.Activities.AgileTestPlatformSpec)]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                  <mtbwa:FindMatchingFiles DisplayName="Find Visual Studio Test Platform Test Assemblies" MatchPattern="[String.Format(&quot;{0}\{1}&quot;, outputDirectory, agileTestPlatformAssembly.AssemblyFileSpec)]" Result="[agileTestPlatformAssemblies]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                  <If Condition="[agileTestPlatformAssemblies.Count() &gt; 0]" DisplayName="If Visual Studio Test Platform Test Assemblies Found" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                    <If.Then>
                                                      <If Condition="[agileTestPlatformAssembly.HasRunSettingsFile]" DisplayName="If agileTestPlatformAssembly.HasRunSettingsFile" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                        <If.Then>
                                                          <Sequence DisplayName="Find Run Settings File And Run Visual Studio Test Runner" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                            <Sequence.Variables>
                                                              <Variable x:TypeArguments="x:String" Name="localRunSettings" />
                                                            </Sequence.Variables>
                                                            <mtbwa:GenerateRunSettings DisplayName="Generate Run Settings File" RunSettingsForTestRun="[agileTestPlatformAssembly.RunSettingsForTestRun]" Result="[localRunSettings]" Workspace="[Workspace]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                            <mtbwa:RunTests DisplayName="Run Visual Studio Test Runner for Test Sources" RunName="[agileTestPlatformAssembly.RunName]" Flavor="[platformConfiguration.Configuration]" Platform="[platformConfiguration.Platform]" TestSources="[agileTestPlatformAssemblies]" RunSettings="[localRunSettings]" TestCaseFilter="[agileTestPlatformAssembly.TestCaseFilter]" ExecutionPlatform="[agileTestPlatformAssembly.ExecutionPlatform]" />
                                                          </Sequence>
                                                        </If.Then>
                                                        <If.Else>
                                                          <mtbwa:RunTests DisplayName="Run Visual Studio Test Runner for Test Sources" RunName="[agileTestPlatformAssembly.RunName]" Flavor="[platformConfiguration.Configuration]" Platform="[platformConfiguration.Platform]" TestSources="[agileTestPlatformAssemblies]" TestCaseFilter="[agileTestPlatformAssembly.TestCaseFilter]" ExecutionPlatform="[agileTestPlatformAssembly.ExecutionPlatform]" />
                                                        </If.Else>
                                                      </If>
                                                    </If.Then>
                                                  </If>
                                                </Sequence>
                                              </If.Then>
                                              <If.Else>
                                                <If Condition="[TypeOf spec Is Microsoft.TeamFoundation.Build.Workflow.Activities.TestMetadataFileSpec]" DisplayName="If spec Is TestMetadataFileSpec" mtbwt:BuildTrackingParticipant.Importance="None">
                                                  <If.Then>
                                                    <Sequence DisplayName="Run MSTest for Metadata File">
                                                      <Sequence.Variables>
                                                        <Variable x:TypeArguments="mtbwa:TestMetadataFileSpec" Name="testMetadataFile" />
                                                        <Variable x:TypeArguments="x:String" Name="localTestMetadata" />
                                                      </Sequence.Variables>
                                                      <Assign x:TypeArguments="mtbwa:TestMetadataFileSpec" DisplayName="Assign spec to testMetadataFile" To="[testMetadataFile]" Value="[DirectCast(spec, Microsoft.TeamFoundation.Build.Workflow.Activities.TestMetadataFileSpec)]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                      <mtbwa:ConvertWorkspaceItem DisplayName="Convert Server Path to Local Path" Input="[testMetadataFile.MetadataFileName]" Result="[localTestMetadata]" Workspace="[Workspace]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                      <mtbwa:MSTest RunTitle="[testMetadataFile.RunName]" Category="[testMetadataFile.CategoryFilter]" DisplayName="Run MSTest for Metadata File" Flavor="[platformConfiguration.Configuration]" MaxPriority="[testMetadataFile.MaximumPriority]" MinPriority="[testMetadataFile.MinimumPriority]" PathToResultsFilesRoot="[TestResultsDirectory]" Platform="[platformConfiguration.Platform]" SearchPathRoot="[outputDirectory]" TestLists="[testMetadataFile.TestLists]" TestMetadata="[localTestMetadata]" TestSettings="[String.Empty]" CommandLineArguments="[testMetadataFile.MSTestCommandLineArgs]" />
                                                    </Sequence>
                                                  </If.Then>
                                                  <If.Else>
                                                    <Sequence DisplayName="Run MSTest for Test Assemblies" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                      <Sequence.Variables>
                                                        <Variable x:TypeArguments="mtbwa:TestAssemblySpec" Name="testAssembly" />
                                                        <Variable x:TypeArguments="scg:IEnumerable(x:String)" Name="testAssemblies" />
                                                        <Variable x:TypeArguments="x:String" Default="[String.Empty]" Name="testFlavor" />
                                                        <Variable x:TypeArguments="x:String" Default="[String.Empty]" Name="testPlatform" />
                                                      </Sequence.Variables>
                                                      <Assign x:TypeArguments="mtbwa:TestAssemblySpec" DisplayName="Assign spec to testAssembly" To="[testAssembly]" Value="[DirectCast(spec, Microsoft.TeamFoundation.Build.Workflow.Activities.TestAssemblySpec)]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                      <mtbwa:FindMatchingFiles DisplayName="Find Test Assemblies" MatchPattern="[String.Format(&quot;{0}\{1}&quot;, outputDirectory, testAssembly.AssemblyFileSpec)]" Result="[testAssemblies]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                      <If Condition="[testAssemblies.Count() &gt; 0]" DisplayName="If Test Assemblies Found" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                        <If.Then>
                                                          <If Condition="[testAssembly.HasTestSettingsFile]" DisplayName="If testAssembly.HasTestSettingsFile" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                            <If.Then>
                                                              <Sequence DisplayName="Find Test Settings File And Run MSTest" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                                <Sequence.Variables>
                                                                  <Variable x:TypeArguments="x:String" Name="localTestSettings" />
                                                                </Sequence.Variables>
                                                                <mtbwa:ConvertWorkspaceItem DisplayName="Convert Server Path to Local Path" Input="[testAssembly.TestSettingsFileName]" Result="[localTestSettings]" Workspace="[Workspace]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                                <mtbwa:MSTest RunTitle="[testAssembly.RunName]" Category="[testAssembly.CategoryFilter]" DisplayName="Run MSTest for Test Assemblies" Flavor="[platformConfiguration.Configuration]" MaxPriority="[testAssembly.MaximumPriority]" MinPriority="[testAssembly.MinimumPriority]" PathToResultsFilesRoot="[TestResultsDirectory]" Platform="[platformConfiguration.Platform]" SearchPathRoot="[outputDirectory]" TestContainers="[testAssemblies]" TestSettings="[localTestSettings]" CommandLineArguments="[testAssembly.MSTestCommandLineArgs]" />
                                                              </Sequence>
                                                            </If.Then>
                                                            <If.Else>
                                                              <mtbwa:MSTest RunTitle="[testAssembly.RunName]" Category="[testAssembly.CategoryFilter]" DisplayName="Run MSTest for Test Assemblies" Flavor="[platformConfiguration.Configuration]" MaxPriority="[testAssembly.MaximumPriority]" MinPriority="[testAssembly.MinimumPriority]" PathToResultsFilesRoot="[TestResultsDirectory]" Platform="[platformConfiguration.Platform]" SearchPathRoot="[outputDirectory]" TestContainers="[testAssemblies]" CommandLineArguments="[testAssembly.MSTestCommandLineArgs]" />
                                                            </If.Else>
                                                          </If>
                                                        </If.Then>
                                                      </If>
                                                    </Sequence>
                                                  </If.Else>
                                                </If>
                                              </If.Else>
                                            </If>
                                          </TryCatch.Try>
                                          <TryCatch.Catches>
                                            <Catch x:TypeArguments="s:Exception">
                                              <ActivityAction x:TypeArguments="s:Exception">
                                                <ActivityAction.Argument>
                                                  <DelegateInArgument x:TypeArguments="s:Exception" Name="testException" />
                                                </ActivityAction.Argument>
                                                <Sequence DisplayName="Handle Test Run Exception">
                                                  <Sequence.Variables>
                                                    <Variable x:TypeArguments="scg:ICollection(mtbc:IQueuedBuild)" Name="failedRequests" />
                                                  </Sequence.Variables>
                                                  <If Condition="[Not (TypeOf testException Is Microsoft.TeamFoundation.Build.Workflow.Activities.TestFailureException)]" DisplayName="If testException is NOT TestFailureException" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                    <If.Then>
                                                      <mtbwa:WriteBuildError DisplayName="Write Test Failure Message" Message="[testException.Message]" />
                                                    </If.Then>
                                                  </If>
                                                  <mtbwa:SetBuildProperties DisplayName="Set TestStatus to Failed" PropertiesToSet="TestStatus" TestStatus="[Microsoft.TeamFoundation.Build.Client.BuildPhaseStatus.Failed]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                  <If Condition="[spec.FailBuildOnFailure]" DisplayName="If spec.FailBuildOnFailure" mtbwt:BuildTrackingParticipant.Importance="Low">
                                                    <If.Then>
                                                      <Assign x:TypeArguments="s:Boolean" DisplayName="Set treatTestFailureAsBuildFailure to True" To="[treatTestFailureAsBuildFailure]" Value="[True]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                    </If.Then>
                                                  </If>
                                                  <mtbwa:GetApprovedRequests DisplayName="Get Requests Approved for Check In" Result="[failedRequests]" mtbwt:BuildTrackingParticipant.Importance="None" />
                                                  <mtbwa:RetryRequests Behavior="[Microsoft.TeamFoundation.Build.Workflow.Activities.RetryBehavior.DoNotBatch]" DisplayName="Mark Requests for Retry" Requests="[failedRequests]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                                                </Sequence>
                                              </ActivityAction>
                                            </Catch>
                                          </TryCatch.Catches>
                                        </TryCatch>
                                      </ActivityAction>
                                    </ForEach>
                                  </If.Then>
                                </If>
                              </Sequence>
                            </If.Then>
                            <If.Else>
                              <If Condition="[(Not TestSpecs Is Nothing) And (TestSpecs.Count &gt; 0)]" DisplayName="If TestSpecs Is Not Nothing or Empty" mtbwt:BuildTrackingParticipant.Importance="Low">
                                <If.Then>
                                  <mtbwa:WriteBuildWarning DisplayName="Write Warning" Message="No automated tests will be run for this build because tests have been disabled for this build definition. To enable these tests, edit this build definition and set the Disable Tests process parameter to false." />
                                </If.Then>
                              </If>
                            </If.Else>
                          </If>
                        </Sequence>
                      </ActivityAction>
                    </ForEach>
                    <If Condition="[BuildDetail.CompilationStatus = Microsoft.TeamFoundation.Build.Client.BuildPhaseStatus.Unknown]" DisplayName="If CompilationStatus = Unknown" mtbwt:BuildTrackingParticipant.Importance="Low">
                      <If.Then>
                        <mtbwa:SetBuildProperties CompilationStatus="[Microsoft.TeamFoundation.Build.Client.BuildPhaseStatus.Succeeded]" DisplayName="Set CompilationStatus to Succeeded" PropertiesToSet="CompilationStatus" mtbwt:BuildTrackingParticipant.Importance="Low" />
                      </If.Then>
                    </If>
                    <If Condition="[BuildDetail.TestStatus = Microsoft.TeamFoundation.Build.Client.BuildPhaseStatus.Unknown]" DisplayName="If TestStatus = Unknown" mtbwt:BuildTrackingParticipant.Importance="Low">
                      <If.Then>
                        <mtbwa:SetBuildProperties DisplayName="Set TestStatus to Succeeded" PropertiesToSet="TestStatus" TestStatus="[Microsoft.TeamFoundation.Build.Client.BuildPhaseStatus.Succeeded]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                      </If.Then>
                    </If>
                    <If Condition="[treatTestFailureAsBuildFailure And (BuildDetail.TestStatus = Microsoft.TeamFoundation.Build.Client.BuildPhaseStatus.Failed)]" DisplayName="If TreatTestFailureAsBuildFailure And (TestStatus = Failed)" mtbwt:BuildTrackingParticipant.Importance="Low">
                      <If.Then>
                        <mtbwa:SetBuildProperties DisplayName="Set Status to Failed" PropertiesToSet="Status" Status="[Microsoft.TeamFoundation.Build.Client.BuildStatus.Failed]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                      </If.Then>
                    </If>
                  </Sequence>
                </TryCatch.Try>
                <TryCatch.Catches>
                  <Catch x:TypeArguments="s:Exception">
                    <ActivityAction x:TypeArguments="s:Exception">
                      <ActivityAction.Argument>
                        <DelegateInArgument x:TypeArguments="s:Exception" Name="compilationExceptionArgument" />
                      </ActivityAction.Argument>
                      <Assign x:TypeArguments="s:Exception" DisplayName="Save the Compilation Exception" To="[compilationException]" Value="[compilationExceptionArgument]" mtbwt:BuildTrackingParticipant.Importance="None" />
                    </ActivityAction>
                  </Catch>
                </TryCatch.Catches>
              </TryCatch>
              <If Condition="[AssociateChangesetsAndWorkItems]" DisplayName="If AssociateChangesetsAndWorkItems" mtbwt:BuildTrackingParticipant.Importance="Low">
                <If.Then>
                  <If Condition="[CreateLabel]" DisplayName="If CreateLabel and AssociateChangesetsAndWorkItems" mtbwt:BuildTrackingParticipant.Importance="Low">
                    <If.Then>
                      <mtbwa:InvokeForReason DisplayName="Associate Changesets and Work Items for non-Shelveset Builds" Reason="Manual, IndividualCI, BatchedCI, Schedule, ScheduleForced, UserCreated">
                        <mtbwa:AssociateChangesetsAndWorkItems DisplayName="Associate Changesets and Work Items" Result="[associatedChangesets]" />
                      </mtbwa:InvokeForReason>
                    </If.Then>
                    <If.Else>
                      <mtbwa:WriteBuildWarning DisplayName="Write Associate Changesets and Work Items Warning" Message="Cannot Associate Changesets and Work Items because the Label Sources option is set to False." />
                    </If.Else>
                  </If>
                </If.Then>
              </If>
            </Parallel>
            <If Condition="[Not compilationException Is Nothing]" DisplayName="If a Compilation Exception Occurred" mtbwt:BuildTrackingParticipant.Importance="Low">
              <If.Then>
                <Throw DisplayName="Rethrow Compilation Exception" Exception="[compilationException]" mtbwt:BuildTrackingParticipant.Importance="Low" />
              </If.Then>
            </If>
            <Parallel DisplayName="Get Impacted Tests, Index Sources and Publish Symbols">
              <If Condition="[PerformTestImpactAnalysis]" DisplayName="If PerformTestImpactAnalysis" mtbwt:BuildTrackingParticipant.Importance="Low">
                <If.Then>
                  <Sequence DisplayName="Get Impacted Tests" mtbwt:BuildTrackingParticipant.Importance="Low">
                    <Sequence.Variables>
                      <Variable x:TypeArguments="scg:IEnumerable(x:String)" Name="assemblies" />
                    </Sequence.Variables>
                    <mtbwa:FindMatchingFiles DisplayName="Find Build Outputs" MatchPattern="[String.Format(&quot;{0}\**\*.dll;{0}\**\*.exe&quot;, BinariesDirectory)]" Result="[assemblies]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                    <mttbb:GetImpactedTests Assemblies="[assemblies]" AssociatedChangesets="[associatedChangesets]" BinariesRoot="[BinariesDirectory]" Build="[BuildDetail]" CodeChanges="{x:Null}" DisplayName="Get Impacted Tests" ImpactedTests="{x:Null}" Workspace="[Workspace]" />
                  </Sequence>
                </If.Then>
              </If>
              <If Condition="[SourceAndSymbolServerSettings.IndexSources Or SourceAndSymbolServerSettings.HasSymbolStorePath]" DisplayName="If SourceAndSymbolServerSettings.IndexSources Or SourceAndSymbolServerSettings.HasSymbolStorePath" mtbwt:BuildTrackingParticipant.Importance="Low">
                <If.Then>
                  <mtbwa:InvokeForReason DisplayName="Index Sources and Publish Symbols for Triggered Builds" Reason="Triggered">
                    <mtbwa:InvokeForReason.Variables>
                      <Variable x:TypeArguments="scg:IEnumerable(x:String)" Name="symbolFiles" />
                    </mtbwa:InvokeForReason.Variables>
                    <mtbwa:FindMatchingFiles DisplayName="Find Symbol Files" MatchPattern="[String.Format(&quot;{0}\**\*.pdb&quot;, BinariesDirectory)]" Result="[symbolFiles]" mtbwt:BuildTrackingParticipant.Importance="Low" />
                    <If Condition="[SourceAndSymbolServerSettings.IndexSources]" DisplayName="If SourceAndSymbolServerSettings.IndexSources" mtbwt:BuildTrackingParticipant.Importance="Low">
                      <If.Then>
                        <TryCatch DisplayName="Try Index Sources" mtbwt:BuildTrackingParticipant.Importance="Low">
                          <TryCatch.Try>
                            <mtbwa:IndexSources DisplayName="Index Sources" FileList="[symbolFiles]" />
                          </TryCatch.Try>
                          <TryCatch.Catches>
                            <Catch x:TypeArguments="s:Exception">
                              <ActivityAction x:TypeArguments="s:Exception">
                                <ActivityAction.Argument>
                                  <DelegateInArgument x:TypeArguments="s:Exception" Name="exception" />
                                </ActivityAction.Argument>
                                <mtbwa:WriteBuildError DisplayName="Write Indexing Sources Error" Message="[exception.Message]" />
                              </ActivityAction>
                            </Catch>
                          </TryCatch.Catches>
                        </TryCatch>
                      </If.Then>
                    </If>
                    <If Condition="[SourceAndSymbolServerSettings.HasSymbolStorePath]" DisplayName="If SourceAndSymbolServerSettings.HasSymbolStorePath" mtbwt:BuildTrackingParticipant.Importance="Low">
                      <If.Then>
                        <TryCatch DisplayName="Try Publish Symbols" mtbwt:BuildTrackingParticipant.Importance="Low">
                          <TryCatch.Try>
                            <mtbwa:SharedResourceScope DisplayName="Synchronize Access to Symbol Store" MaxExecutionTime="[TimeSpan.Zero]" MaxWaitTime="[New TimeSpan(1, 0, 0)]" ResourceName="[SourceAndSymbolServerSettings.SymbolStorePath]" mtbwt:BuildTrackingParticipant.Importance="Low">
                              <mtbwa:PublishSymbols DisplayName="Publish Symbols" FileList="[symbolFiles]" ProductName="[BuildDetail.BuildDefinition.Name]" StorePath="[SourceAndSymbolServerSettings.SymbolStorePath]" Version="[BuildDetail.BuildNumber]" />
                            </mtbwa:SharedResourceScope>
                          </TryCatch.Try>
                          <TryCatch.Catches>
                            <Catch x:TypeArguments="s:Exception">
                              <ActivityAction x:TypeArguments="s:Exception">
                                <ActivityAction.Argument>
                                  <DelegateInArgument x:TypeArguments="s:Exception" Name="exception" />
                                </ActivityAction.Argument>
                                <mtbwa:WriteBuildError DisplayName="Write Publishing Symbols Error" Message="[exception.Message]" />
                              </ActivityAction>
                            </Catch>
                          </TryCatch.Catches>
                        </TryCatch>
                      </If.Then>
                    </If>
                  </mtbwa:InvokeForReason>
                </If.Then>
              </If>
            </Parallel>
          </Sequence>
        </TryCatch.Try>
      </TryCatch>
    </mtbwa:AgentScope>
    <mtbwa:InvokeForReason DisplayName="Check In Gated Changes for CheckInShelveset Builds" Reason="CheckInShelveset">
      <mtbwa:CheckInGatedChanges DisplayName="Check In Gated Changes" />
    </mtbwa:InvokeForReason>
  </Sequence>
</Activity>
