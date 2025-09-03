What is FlatList ?
It is a component of react native that is used to render the list of data in performant manner supporting features like -
optional horizontal scroll
refresh onload
Multiple column support
Header and Footer support
fully cross platforms

Props to be used - 
1. numColumns
2. By passing extraData={selectedId} to FlatList we make sure FlatList itself will re-render when the state changes. Without setting this prop, FlatList would not know it needs to re-render any items because it is a PureComponent and the prop comparison will not show any changes.
keyExtractor tells the list to use the ids for the react keys instead of the default key property.
3. ListFooterComponent
4. ListFooterComponentStyle
5. data (required)
6. ListEmptyComponent
7. ItemSeparatorComponent
8. renderItem (required)
9. extraData
A marker property for telling the list to re-render (since it implements PureComponent). If any of your renderItem, Header, Footer, etc. functions depend on anything outside of the data prop, stick it here and treat it immutable
10. horizontal
11. initialNumToRender = 10 