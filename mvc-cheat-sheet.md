# MVC5 Forms
## Bootstrap Styling Form Sample
````
/* Using BeginForm wraps from and maps post to Save action on CustomersController*/
@using (Html.BeginForm("Save", "Customers"))
{
   
	@Html.HiddenFor(m => m.Customer.Id)
	/* Pairs enclosed in form-group divs (for bootstrap stying)*/
	/* Html helpers used to render controls w/ @class="form-control" for bootstrap styling */
    <div class="form-group">
        @Html.LabelFor(m => m.Customer.Name)
        @Html.TextBoxFor(m => m.Customer.Name, new { @class = "form-control" })
    </div>
    <div class="form-group">
        @Html.LabelFor(m => m.Customer.BirthDate)
        @Html.TextBoxFor(m => m.Customer.BirthDate, "{0:d}", new { @class = "form-control" })
    </div>
    <div class="form-group">
        @Html.LabelFor(m => m.Customer.MembershipTypeId)
        @Html.DropDownListFor(m => m.Customer.MembershipTypeId, new SelectList(Model.MembershipTypes, "Id", "Name"), "Select One", new { @class = "form-control" })
    </div>
	/* Checkbox is constructed a bit differently for poper bootstrap styling */
    <div class="checkbox">
        <label>
            @Html.CheckBoxFor(m => m.Customer.IsSubscribedToNewsletter) <text>@Html.LabelFor(m => m.Customer.IsSubscribedToNewsletter)</text>
        </label>
    </div>
    /* Button classes of btn bun-primary for bootstrap styling of default button */
    <button type="submit" class="btn btn-primary">Save</button>
}
````
