# dynamic-menu-angular
Dynamically creates the menu by fetching the configuration from backend

app_menu table

![app_menu#1](image.png)
![app_menu#2](image-1.png)

## Menu Options
### Side Menu
It is a dynamic accordion which slides out from the left on click of menu button.

![side-menu](image-2.png)

### Shortcut Menu
It is a dynamic home screen customizable shortcuts.

![shortcuts](image-3.png)

## Dashboard Sample

### Default Theme

![alt text](image-4.png)

### Deep Ocean Theme

![alt text](image-5.png)

### Deep Space Theme

![alt text](image-6.png)

### Theme Switcher

![alt text](image-7.png)




# Code Samples
## Side Menu

```ts
\\model.ts
export interface MenuItem {
menuCode:string;
menuIcon:any;
displayName:string;
menuType:string;
menuUrl:string;
sequence:number;
disabled:Boolean;
infoText:string;
customCss:any;
functionName;string;
childMenus;
}
```

```html
<! Dynamic Accordian Population>
<mat-accordion #navMenu="matAccordion" [displayMode]="displayMode" [multi]="multi" class="app-nav-accordion">
      <span *ngFor="let menuItem of sideMenuItems">
      <mat-nav-list>
        <button *ngIf="menuItem.childMenus.length == 0" routerLink="{{menuItem.menuUrl}}" (click)="resolve(menuItem.functionName)" mat-menu-item>
          <mat-icon *ngIf="menuItem.menuIcon.type == 'matIcon'">{{menuItem.menuIcon.name}}</mat-icon>
          <span>{{menuItem.displayName}}</span>
        </button>
      </mat-nav-list>
      <mat-expansion-panel *ngIf="menuItem.childMenus.length > 0" class="mat-elevation-z0">
        <mat-expansion-panel-header class="py-0 pl-0 pr-4">
          <span mat-menu-item>
            <mat-icon *ngIf="menuItem.menuIcon.type == 'matIcon'">{{menuItem.menuIcon.name}}</mat-icon>
            <span>{{menuItem.displayName}}</span>
          </span>
        </mat-expansion-panel-header>
        <mat-nav-list class="p-0">
            <span  style="font-family: 'Baloo Thambi 2', cursive" *ngFor="let childMenu of menuItem.childMenus" mat-menu-item routerLink="{{childMenu.menuUrl}}" (click)="resolve(childMenu.functionName)">{{childMenu.displayName}}</span>
        </mat-nav-list>
    </mat-expansion-panel>
    </span>
    </mat-accordion>
    ```

