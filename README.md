# show-scrollbar-chat-xamarin-forms
This sample demonstrates how to show the ScrollBar in Xamarin.Forms Chat (SfChat).

## Sample

```xaml

    <ContentPage.Content>
        <sfChat:SfChat x:Name="sfChat"
                       Messages="{Binding Messages}"
                       CurrentUser="{Binding CurrentUser}"   
                       ShowIncomingMessageAvatar="True"
                       ShowOutgoingMessageAvatar="True">
            <sfChat:SfChat.Behaviors>
                <local:SfchatBehaviors/>
            </sfChat:SfChat.Behaviors>
        </sfChat:SfChat>
    </ContentPage.Content>

Behavior:

    public class SfchatBehaviors : Behavior<SfChat>
    {
        #region Fields

        private SfChat sfChat = null;
        private SfListView ChatListView = null;

        #endregion

        #region Overrides

        protected override void OnAttachedTo(SfChat bindable)
        {
            base.OnAttachedTo(bindable);
            sfChat = bindable;
            if (sfChat != null)
            {
               ChatListView = (sfChat.GetType().GetRuntimeProperties().FirstOrDefault(x => x.Name.Equals("ChatListView")).GetValue(sfChat) as SfListView);
                if (ChatListView != null)
                {
                    ChatListView.IsScrollBarVisible = true;
                }
            }
        }

        protected override void OnDetachingFrom(SfChat bindable)
        {
            base.OnAttachedTo(bindable);
            ChatListView = null;
            sfChat = null;
        }

        #endregion
    }
    
```
## Requirements to run the demo

To run the demo, refer to [System Requirements for Xamarin](https://help.syncfusion.com/xamarin/system-requirements)

## Troubleshooting

### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.


